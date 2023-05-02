#include <stdio.h>
#include <string.h>

int main() {
    char str[100];
    int len, freq = 0;
    printf("Enter a string: ");
    scanf("%s", str);
    len = strlen(str);
    printf("Length of the string is: %d\n", len);
    
    // calculate word frequency
    for (int i = 0; i < len; i++) {
        if (str[i] != ' ') {
            freq++;
            while (str[i] != ' ' && i < len) {
                i++;
            }
        }
    }
    printf("Word frequency is: %d\n", freq);
    
    // find first repeated and non-repeated characters
    char *ptr1, *ptr2;
    ptr1 = str;
    ptr2 = str + 1;
    char *rep = NULL, *non_rep = NULL;
    while (*ptr1 != '\0' && rep == NULL) {
        while (*ptr2 != '\0' && rep == NULL) {
            if (*ptr1 == *ptr2) {
                rep = ptr1;
            }
            ptr2++;
        }
        if (rep == NULL && non_rep == NULL) {
            non_rep = ptr1;
        }
        ptr1++;
        ptr2 = ptr1 + 1;
    }
    if (rep == NULL) {
        printf("No repeated characters found in the string.\n");
    }
    else {
        printf("First repeated character is: %c\n", *rep);
    }
    if (non_rep == NULL) {
        printf("No non-repeated characters found in the string.\n");
    }
    else {
        printf("First non-repeated character is: %c\n", *non_rep);
    }
    return 0;
}
