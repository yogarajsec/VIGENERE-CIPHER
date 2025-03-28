# VIGENERE-CIPHER
## EX. NO: 1(D)
 

## IMPLEMETATION OF VIGENERE CIPHER
 

## AIM:

To implement the Vigenere Cipher substitution technique using C program.

## DESCRIPTION:

To encrypt, a table of alphabets can be used, termed a tabula recta, Vigenère square,or Vigenère table. It consists of the alphabet written out 26 times in differnt rows, each
 
alphabet shifted cyclically to the left compared to the previous alphabet, corresponding to the 26 possible Caesar ciphers. At different points in the encryption process, the cipher uses adifferent alphabet from one of the rows. The alphabet used at each point repeating keyword.depends on a Each row starts with a key letter. The remainder of the row holds the letters A to Z. Although there are 26 key rows shown, you will only use as many keys as there are unique letters in the key string, here just 5 keys, {L, E, M, O, N}. For successive letters of the message, we are going to take successive letters of the key string, and encipher each message letter using its corresponding key row. Choose the next letter of the key, go along that row to find the column heading that	atches the message character; the letter at the intersection of
[key-row, msg-col] is the enciphered letter.


## ALGORITHM:

STEP-1: Arrange the alphabets in row and column of a 26*26 matrix.
STEP-2: Circulate the alphabets in each row to position left such that the first letter is attached to last.
STEP-3: Repeat this process for all 26 rows and construct the final key matrix.
STEP-4: The keyword and the plain text is read from the user.
STEP-5: The characters in the keyword are repeated sequentially so as to match with that of the plain text.
STEP-6: Pick the first letter of the plain text and that of the keyword as the row indices and column indices respectively.
STEP-7: The junction character where these two meet forms the cipher character.
STEP-8: Repeat the above steps to generate the entire cipher text.


## PROGRAM
```
#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <stdlib.h>

void encrypt() {
char plaintext[128];
char key[16];
printf("\nEnter the plaintext (up to 128 characters): ");
scanf(" %[^\n]", plaintext); // Read input with spaces
printf("Enter the key (up to 16 characters): ");
scanf(" %[^\n]", key);

printf("Cipher Text: ");  
for (int i = 0, j = 0; i < strlen(plaintext); i++, j++) {  
    if (j >= strlen(key)) {  
        j = 0;  
    }  
    int shift = toupper(key[j]) - 'A';  
    char encryptedChar = ((toupper(plaintext[i]) - 'A' + shift) % 26) + 'A';  
    printf("%c", encryptedChar);  
}  
printf("\n");  
}

void decrypt() {
char ciphertext[128];
char key[16];
printf("\nEnter the ciphertext: ");
scanf(" %[^\n]", ciphertext);
printf("Enter the key: ");
scanf(" %[^\n]", key);

printf("Deciphered Text: ");  
for (int i = 0, j = 0; i < strlen(ciphertext); i++, j++) {  
    if (j >= strlen(key)) {  
        j = 0;  
    }  
    int shift = toupper(key[j]) - 'A';  
    char decryptedChar = ((toupper(ciphertext[i]) - 'A' - shift + 26) % 26) + 'A';  
    printf("%c", decryptedChar);  
}  
printf("\n");  
}

int main() {
int option;
while (1) {
printf("\n1. Encrypt");
printf("\n2. Decrypt");
printf("\n3. Exit\n");
printf("\nEnter your option: ");
scanf("%d", &option);

    switch (option) {  
        case 1:  
            encrypt();  
            break;  
        case 2:  
            decrypt();  
            break;  
        case 3:  
            exit(0);  
        default:  
            printf("\nInvalid selection! Try again.\n");  
            break;  
    }  
}  
return 0;  
}
```

## OUTPUT
![Screenshot 2025-03-28 160213](https://github.com/user-attachments/assets/7f9ecc42-6ee7-4920-aa46-6f6ac8ee1d93)

## RESULT
Thus the C program for Vigenere Cipher is implemented successfully.
