---
title: "Incremental backups and full disk encryption"
date: 2011-02-23
forum: Desktop Environments
---

### Post by visual1ce on 2011-02-23
How should I go about backing up data to an external 40GB USB HDD from 120GB internal? I have full disk encryption so backing up to a non-encrypted drive is not an option.

I can configure the external drive with an encrypted partition but I don't want to create a different passphrase. Is it a bad idea to encrypt the drive with the same passphrase? If I use a different passphrase I will most likely forget or lose it since I figure I will rarely use it (probably store it in keyring - is this a bad idea?) If my hdd fails then I lose the passphrase stored in keyring and my backups become useless...

Also looking at luksDump I see a whole lot of information about the encrypted drive. Is it possible to use this information to crack the passphrase?

---

### Post by visual1ce on 2011-02-23
Can someone please move this to a more appropriate category?

---

### Post by Hawkoon on 2011-02-23
> **visual1ce said:**
> Is it a bad idea to encrypt the drive with the same passphrase?

A brute force attack might take less time to be successful if someone got hold of both drives, and access to both drives would be gained.

But it also depends what you are trying to protect against, like a theft or police confiscation scenario. You could scribble down the passphrase some where, where no one is expecting to look for it (which implies that a burglar a) knows that your drive is encrypted and b) has enough time to consider that you wrote down the password and has even more time to look for it - I find that highly unlikely). If you don't trust your own children however, well, then perhaps you should get a much longer passphrase.

> **visual1ce said:**
> 
Also looking at luksDump I see a whole lot of information about the  encrypted drive. Is it possible to use this information to crack the  passphrase?

You noted that it is easy to verify that the drive is encrypted. So in a confiscation scenario police could force you to reveal your password. Truecrypt, a different encryption technology, has been designed to offer what is called plausible deniability. There is supposed to be no difference between a drive overwritten with random data and a truecrypt encrypted drive.

> **visual1ce said:**
> If my hdd fails then I lose the  passphrase stored in keyring and my backups become useless...

I am not sure if you can do this with luks, but with truecrypt you can backup the volume header of an encrypted drive and then change the passphrase. If you forget that new passphrase (or you want to reset it in case you are an admin and provided this drive for a co-worker) you can restore the volume header and use your old passphrase again. You just have to keep that header backup in a safe place.

Again, not sure if this is also a luks option, but truecrypt supports the use of keyfiles as an alternative to passphrases, so you would have to have a certain file sitting somewhere on your system or USB stick to be able to unlock the drive. That might be an option for you as well.

---

