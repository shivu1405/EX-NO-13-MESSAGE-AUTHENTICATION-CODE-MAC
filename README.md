# EX-NO-13-MESSAGE-AUTHENTICATION-CODE-MAC

## AIM:
To implement MESSAGE AUTHENTICATION CODE(MAC)

## ALGORITHM:

1. Message Authentication Code (MAC) is a cryptographic technique used to verify the integrity and authenticity of a message by using a secret key.

2. Initialization:
   - Choose a cryptographic hash function \( H \) (e.g., SHA-256) and a secret key \( K \).
   - The message \( M \) to be authenticated is input along with the secret key \( K \).

3. MAC Generation:
   - Compute the MAC by applying the hash function to the combination of the message \( M \) and the secret key \( K \): 
     \[
     \text{MAC}(M, K) = H(K || M)
     \]
     where \( || \) denotes concatenation of \( K \) and \( M \).

4. Verification:
   - The recipient, who knows the secret key \( K \), computes the MAC using the received message \( M \) and the same hash function.
   - The recipient compares the computed MAC with the received MAC. If they match, the message is authentic and unchanged.

5. Security: The security of the MAC relies on the secret key \( K \) and the strength of the hash function \( H \), ensuring that an attacker cannot forge a valid MAC without knowledge of the key.

## Program:
```
#include <stdio.h>
#include <string.h>

// Simple MAC using XOR for demonstration
int main()
{
    char message[100], key[100], mac[100];
    int i, len;

    printf("Enter the message: ");
    scanf("%s", message);

    printf("Enter the secret key: ");
    scanf("%s", key);

    len = strlen(message);

    // Generate MAC
    for(i = 0; i < len; i++)
    {
        mac[i] = message[i] ^ key[i % strlen(key)];
    }
    mac[len] = '\0';

    printf("\nGenerated MAC: ");
    for(i = 0; i < len; i++)
    {
        printf("%02X", mac[i]);
    }

    printf("\n");

    return 0;
}
```


## Output:


## Result:
The program is executed successfully.
