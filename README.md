# HILL CIPHER
HILL CIPHER
EX. NO: 3 AIM:
 

IMPLEMENTATION OF HILL CIPHER
 
## To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. STEP-2: Split the plain text into groups of length three. STEP-3: Arrange the keyword in a 3*3 matrix.
STEP-4: Multiply the two matrices to obtain the cipher text of length three.
STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 
~~~
#include <stdio.h>
#include <string.h>
#include <ctype.h>
int keyMatrix[3][3] = {
 { 1, 2, 1 },
 { 2, 3, 2 },
 { 2, 2, 1 }
};
int inverseKeyMatrix[3][3] = {
 { -1, 0, 1 },
 { 2, -1, 0 },
 { -2, 2, -1 }
};
char alphabet[] = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
void encryptBlock(char p1, char p2, char p3, char result[]) {
 int pos1 = p1 - 'A';
 int pos2 = p2 - 'A';
 int pos3 = p3 - 'A';
 int c1 = pos1 * keyMatrix[0][0] + pos2 * keyMatrix[1][0] + pos3 * keyMatrix[2][0];
 int c2 = pos1 * keyMatrix[0][1] + pos2 * keyMatrix[1][1] + pos3 * keyMatrix[2][1];
 int c3 = pos1 * keyMatrix[0][2] + pos2 * keyMatrix[1][2] + pos3 * keyMatrix[2][2];
 result[0] = alphabet[c1 % 26];
 result[1] = alphabet[c2 % 26];
 result[2] = alphabet[c3 % 26];
 result[3] = '\0';
}
void decryptBlock(char c1, char c2, char c3, char result[]) {
 int pos1 = c1 - 'A';
 int pos2 = c2 - 'A';
 int pos3 = c3 - 'A';
 int p1 = pos1 * inverseKeyMatrix[0][0] + pos2 * inverseKeyMatrix[1][0] + pos3 *
inverseKeyMatrix[2][0];
 int p2 = pos1 * inverseKeyMatrix[0][1] + pos2 * inverseKeyMatrix[1][1] + pos3 *
inverseKeyMatrix[2][1];
 int p3 = pos1 * inverseKeyMatrix[0][2] + pos2 * inverseKeyMatrix[1][2] + pos3 *
inverseKeyMatrix[2][2];
 result[0] = alphabet[(p1 % 26 < 0) ? (26 + p1 % 26) : (p1 % 26)];
 result[1] = alphabet[(p2 % 26 < 0) ? (26 + p2 % 26) : (p2 % 26)];
 result[2] = alphabet[(p3 % 26 < 0) ? (26 + p3 % 26) : (p3 % 26)];
 result[3] = '\0';
}
int main() {
 char plaintext[1000];
 char ciphertext[1000] = "";
 char decrypted[1000] = "";
 char block[4];
 int remainder;
 printf("Enter plaintext : ");
 scanf("%s", plaintext);
 for (int i = 0; i < strlen(plaintext); i++) {
 plaintext[i] = toupper(plaintext[i]);
 }

 remainder = strlen(plaintext) % 3;
 if (remainder != 0) {
 for (int i = 1; i <= (3 - remainder); i++) {
 strcat(plaintext, "X");
 }
 }
 for (int i = 0; i < strlen(plaintext); i += 3) {
 encryptBlock(plaintext[i], plaintext[i + 1], plaintext[i + 2], block);
 strcat(ciphertext, block);
 }
 printf("Ciphertext: %s\n", ciphertext);
 for (int i = 0; i < strlen(ciphertext); i += 3) {
 decryptBlock(ciphertext[i], ciphertext[i + 1], ciphertext[i + 2], block);
 strcat(decrypted, block);
 }
 printf("Decrypted plaintext: %s\n", decrypted);
 return 0;
}
~~~
## OUTPUT
<img width="606" height="277" alt="image" src="https://github.com/user-attachments/assets/092a3a62-3a34-41c7-94ea-22e47249a764" />

## RESULT
Thus,hill cipher has been successfully implemented.
