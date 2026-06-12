---
title: "GnuPG: where's my private PGP key"
date: 2009-01-07
forum: General Help
---

### Post by jsroth on 2009-01-07
Since my ubuntu isn't booting at the moment and I don't seem to find a solution to this I'm thinking about reinstalling it. Unfortunately I forgot to backup my private PGP key which I used with GnuPG and Enigmail etc. Is there a way to recover it (I know all my passwords/-phrases)?

Thanks for your help!

---

### Post by heindsight on 2009-01-07
if you can boot from a live cd, you can mount the partition containing your home directory and then back up the .gnupg directory from your home directory, then after you reinstall you can just restore the backed up .gnupg

---

### Post by jsroth on 2009-01-07
There seems to be no .gnupg in the home directory. Is there any other place the date could be saved? (And yes I know how to find the hidden folders ;))

---

### Post by heindsight on 2009-01-07
strange, i have no idea where else it could be. perhaps try searching for a file called secring.gpg within your home directory.

---

### Post by todak on 2009-01-07
Nevermind. I should read first!

---

### Post by jsroth on 2009-01-08
I'm not sure what to think about it, but i found a secring.pgp in /etc/apt/ no idea why there is one in that directory. But I'm going to give it a go ...

---

### Post by heindsight on 2009-01-08
/etc/apt/secring.gpg is most probably empty and the other .gpg files in /etc/apt contain public keys for the repositories and are used by *apt* to verify the keys used to sign packages. your personal keys will be somewhere in your home directory.

I just googled 'enigmail gpg' and found this: [http://enigmail.mozdev.org/documentation/gpgsetup.php#backup](http://enigmail.mozdev.org/documentation/gpgsetup.php#backup)
If you could boot your normal ubuntu installation you could run ```
gpg --version
``` and look for a line starting with ```
Home:
``` in the output which would indicate where your key files are located.

Since you can not boot normally the only solution is still to find a secring.pgp (which is the file containing your private key) somewhere in your home directory.

---

### Post by sockrebel on 2009-01-08
> **jsroth said:**
> There seems to be no .gnupg in the home directory. Is there any other place the date could be saved? (And yes I know how to find the hidden folders ;))

Did you look in the home directory of the live cd or on your computer? (ie... Did you mount the hard drive partition?)

Just checking. ;-)

---

### Post by jsroth on 2009-01-09
I did look in the mounted directory ... but that was a good idea ;)

And I couldn't find the secring.pgp anywhere in the home directory, so I revoked my key and got a new one, annoying but ... happens.

Thanks for all your help!

---

