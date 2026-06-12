---
title: "Getting a SHA-1 hash"
date: 2008-12-17
forum: General Help
---

### Post by pwaugh on 2008-12-17
Guys, is UTF-8 the default character format?

I'm trying to use SHA-1 to get a nicely formated Long from a string using something like this:

```
/*
 Generate a Message Digest
*/
import java.security.*;
import javax.crypto.*;

public class MessageDigestExample {
    
    public static void main (String[] args) throws Exception {
        //
        // Check args and get plaintext
        if (args.length !=1) {
            System.err.println("Usage: java MessageDigestExample text");
            System.exit(1);
        }

        byte[] plainText = args[0].getBytes("UTF8");
        //
        // Get a message digest object using the MD2 algorithm  BOUNCY
        //MessageDigest messageDigest = MessageDigest.getInstance("MD2");
        //
        // Get a message digest object using the MD5 algorithm
        //MessageDigest messageDigest = MessageDigest.getInstance("MD5");
        //
        // Get a message digest object using the SHA-1 algorithm
        MessageDigest messageDigest = MessageDigest.getInstance("SHA-1");                        
        //
        // Get a message digest object using the SHA-256 algorithm
        // MessageDigest messageDigest = MessageDigest.getInstance("SHA-256");
        //
        // Get a message digest object using the SHA-384 algorithm
        // MessageDigest messageDigest = MessageDigest.getInstance("SHA-384");
        //
        // Get a message digest object using the SHA-512 algorithm
        // MessageDigest messageDigest = MessageDigest.getInstance("SHA-512");              
        //
        // Print out the provider used
        System.out.println( "\n" + messageDigest.getProvider().getInfo() );
        //
        // Calculate the digest and print it out
        messageDigest.update( plainText);
        System.out.println( "\nDigest: " );
        System.out.println( new String( messageDigest.digest(), "UTF8") );

    }
}

```

but I'm getting graphics characters rather than something like "0x123456789ABCDEFL"

Obviously, I'll have to put in the "0x" and "L", but that's the format I'm looking for and I'm not sure about this UTF-8 thing.

---

