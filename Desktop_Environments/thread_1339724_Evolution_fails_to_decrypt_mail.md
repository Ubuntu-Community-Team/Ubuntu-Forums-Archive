---
title: "Evolution fails to decrypt mail"
date: 2009-11-27
forum: Desktop Environments
---

### Post by tokei on 2009-11-27
Hi, 

I have recently done an upgrade from Ubuntu 8.10 to 9.10. Under 8.10, Evolution could not decrypt MIME mails. Under 9.10, it can't decrypt any mails at all except the ones I sent encrypted and which where encrypted to myself in the sent folder.

On command line, I can decrypt text files, with gpg 1 and 2! Following a tip from another thread, I removed the line "use-agent" from .gnupg/gpg.conf. The password dialog in Evolution looks different now, but I still can't decrypt my mail inside of Evolution.

All it says is the following:

```
Could not parse PGP message
gpg: armor header: Charset: ISO-8859-15
gpg: armor header: Version: GnuPG v1.4.9 (GNU/Linux)
gpg: armor header: Comment: Using GnuPG with Mozilla - http://enigmail.mozdev.org/
gpg: public key is $PUBLIC_ID
gpg: using subkey $PUBLIC_ID instead of primary key $KEY_ID
gpg: using subkey $PUBLIC_ID instead of primary key $KEY_ID
gpg: public key is $SOME_OTHER_ID
gpg: encrypted with RSA key, $SOME_OTHER_ID
gpg: encrypted with 1024-bit ELG-E key, ID $PUBLIC_ID, created 2006-10-25
"tokei <mail@domain.com>"
gpg: AES256 encrypted data
gpg: original file name=''
gpg: Signature made Tue 24 Nov 2009 11:28:43 PM CET using RSA key ID $YET_ANOTHER_ID
gpg: Can't check signature: public key not found
```

Where as on command line it gpg says:

```
You need a passphrase to unlock the secret key for
user: "tokei <mail@domain.com>"
1024-bit ELG key, ID $PUBLIC_ID, created 2006-10-25 (main key ID $KEY_ID)

can't connect to `/home/tokei/.gnupg/S.gpg-agent': No such file or directory
gpg: encrypted with RSA key, ID $SOME_OTHER_ID
gpg: encrypted with 1024-bit ELG key, ID $PUBLIC_ID, created 2006-10-25
      "tokei <mail@domain.com>"
```

...and then goes on decrypting the file.

Versions are:

```
> gpg --version
gpg (GnuPG) 1.4.9

> gpg2 --version
gpg (GnuPG) 2.0.12

> evolution --version
GNOME evolution 2.28.1
```

Any hint on what might be the cause of this and how to fix it would be greatly appreciated. 

tia/tokei

---

