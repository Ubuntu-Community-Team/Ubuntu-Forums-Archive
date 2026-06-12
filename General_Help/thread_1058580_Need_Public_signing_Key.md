---
title: "Need Public signing Key"
date: 2009-02-03
forum: General Help
---

### Post by DougieFresh4U on 2009-02-03
Every once in a while this will show up in terminal on Intrepid machine:
```
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5AFADBD4AA1C92B
```

Can some one please provide key or link to it?
Thanks, Dougie

---

### Post by wolfen69 on 2009-02-03
in terminal:
```
gpg --keyserver keyserver.ubuntu.com --recv 5AFADBD4AA1C92B
gpg --export --armor 5AFADBD4AA1C92B | sudo apt-key add -
```

btw, i'm originally from rochester. now in connecticut.

---

### Post by DougieFresh4U on 2009-02-04
> **wolfen69 said:**
> in terminal:
```
gpg --keyserver keyserver.ubuntu.com --recv 5AFADBD4AA1C92B
gpg --export --armor 5AFADBD4AA1C92B | sudo apt-key add -
```

btw, i'm originally from rochester. now in connecticut.

Tried it and no go
```
dougie@DougiesLeanMachine:~$ gpg --keyserver keyserver.ubuntu.com --recv 5AFADBD4AA1C92B
gpg: "5AFADBD4AA1C92B" not a key ID: skipping

```

```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5AFADBD4AA1C92B0

```

---

### Post by dedeaux on 2009-02-04
I believe the reason you are getting that error is that your key is missing a digit...

5AFADBD4AA1C92B0 should be the correct key.  Give that a try.
```

gpg --keyserver keyserver.ubuntu.com --recv 5AFADBD4AA1C92B0
gpg --export --armor 5AFADBD4AA1C92B0 | sudo apt-key add -
```

---

### Post by DougieFresh4U on 2009-02-05
> **dedeaux said:**
> I believe the reason you are getting that error is that your key is missing a digit...

5AFADBD4AA1C92B0 should be the correct key.  Give that a try.
```

gpg --keyserver keyserver.ubuntu.com --recv 5AFADBD4AA1C92B0
gpg --export --armor 5AFADBD4AA1C92B0 | sudo apt-key add -
```

Thank you very much, as that did the trick.
All set now

---

### Post by forger on 2009-02-07
You also need to change the ppa repository link, I suggest you try:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

