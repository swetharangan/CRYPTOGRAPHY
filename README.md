# CRYPTOGRAPHY
HILL CIPHER
EX. NO: 1(C) AIM:
 

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

int mod26(int x) {
    return (x % 26 + 26) % 26;
}

// Function to multiply 3x3 matrix with a 3x1 vector
void encrypt(int key[3][3], char plain[3], char cipher[3]) {
    int i, j;
    for (i = 0; i < 3; i++) {
        int sum = 0;
        for (j = 0; j < 3; j++) {
            sum += key[i][j] * (plain[j] - 'A');
        }
        cipher[i] = mod26(sum) + 'A';
    }
}

int main() {
    int key[3][3];
    char plain[100], cipher[100];
    int i, j, k = 0, len;

    printf("Enter 9 integers for 3x3 key matrix:\n");
    for (i = 0; i < 3; i++)
        for (j = 0; j < 3; j++)
            scanf("%d", &key[i][j]);

    printf("Enter the plain text (in uppercase): ");
    scanf("%s", plain);

    len = strlen(plain);
    
    // Padding if not multiple of 3
    while (len % 3 != 0) {
        plain[len++] = 'X';
        plain[len] = '\0';
    }

    for (i = 0; i < len; i += 3) {
        char block[3], encrypted[3];
        block[0] = plain[i];
        block[1] = plain[i + 1];
        block[2] = plain[i + 2];
        encrypt(key, block, encrypted);
        cipher[k++] = encrypted[0];
        cipher[k++] = encrypted[1];
        cipher[k++] = encrypted[2];
    }

    cipher[k] = '\0';
    printf("Encrypted Text: %s\n", cipher);

    return 0;
}

~~~

## OUTPUT
![image](https://github.com/user-attachments/assets/45bb4620-507e-4a69-9b73-476c8e4191a3)


## RESULT
Thus, the C program to implement the Hill Cipher was successfully executed and the cipher text was generated.
