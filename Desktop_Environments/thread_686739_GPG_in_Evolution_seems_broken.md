---
title: "GPG in Evolution seems broken?"
date: 2008-02-03
forum: Desktop Environments
---

### Post by OlympicSoftworks on 2008-02-03
Does anyone use Evolution and PGP encryption?

I have been using Gmail, but need to start signing some emails so I would like to use Evolution as my mail client.  Got it to sync w/gmail no prob, but upon reading a message that has an encrypted block of text I get this error that shows up just before the text block in the email.

Could not parse PGP message
gpg: armor header: Version: GnuPG v1.4.2.2 (GNU/Linux)
gpg: public key is ########
gpg: encrypted with ELG-E key, ID ########
gpg: decryption failed: secret key not available

I am using "evolution 2.12.1".  Now, I have pgp set up, keys uploaded and was able to decrypt the block using the terminal commands to do it, but this is not going to be suitable going forward.  Everything I have read says Evolution is set up to do this without any other packages, and indeed, it does recognize that I have a key.  However the key it thinks is public is actually my private key and changing the key in Accounts->Security seems to have no effect.

Am I missing something here, or is there an issue currently with Evolution and PGP?  I could go with Thunderbird and Enigmail as I understand it, but would like to use some of the other functions of Evolution I'd like to get it to work correctly.

Thanks for any help folks.
Dave

---

### Post by jimrz on 2008-02-03
Take a look at [[COLOR="Sienna"]_this_[/COLOR]]("https://help.ubuntu.com/community/GnuPrivacyGuardHowto") , works fine for me. There is also a Firefox extension (FireGPG, I think) that can work with Gmail.

---

### Post by rameez on 2008-05-27
I am getting the same error with evolution, was anyone able to get a fix on this one?
A friend of mine told me that problem is that linux adds LF characters after every line and windows doesn't. 
I am able to open and decrypt these mesages on thunderbird (win and mac os x) but evolution doesn't work.

Rameez.

---

