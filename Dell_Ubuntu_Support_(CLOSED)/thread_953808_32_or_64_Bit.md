---
title: "32 or 64 Bit?"
date: 2008-10-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Corelogik on 2008-10-20
Does anyone know if the version of Ubuntu that comes pre-installed on Dell systems is 32 or 64 Bit?

If it's 64, does anyone know how to install something called "32-bit compatibility environment" for it. One of the games I play (Second Life) has a Linux version, but I guess it doesn't do 64 Bit so well.

TIA
~Core

---

### Post by PC_load_letter on 2008-10-20
I'd bet real money that it is the 32 bit version. It's the most compatible, near hassle-free in setting up flash, codecs...etc. Most software that are developed for Linux (or migrated from Windows e.g. Skype) are usually native 32bit. Besides, 64bit performance would only show when you have enough RAM and that is if it is > 4GB. 

I am not dissing 64bit, I am actually running amd64 Ubuntu on two PCs at home. I'm just saying the 32bit version is the safer choice for a manufacturer like Dell.
My 2 cents.

---

### Post by patrickballeux on 2008-10-20
To validate which architecture was installed on your PC, have a look for the folder /usr/lib32 or /lib64.  If you have this, then this is a 64bits setup.  If not, then you have a 32bits setup.

If you have a 64 bits setup, what you need to install for secondlife is the "ia32-libs" package.  You can look for it using Synaptic or use the command line in a terminal:

```
sudo apt-get install ia32-libs
```

Other packages will be installed as well as being dependencies for the package is32-libs.

Second Life should work after that.

---

### Post by Corelogik on 2008-10-20
Thanks for the info.

---

### Post by jespdj on 2008-10-21
> **patrickballeux said:**
> To validate which architecture was installed on your PC, have a look for the folder /usr/lib32 or /lib64.  If you have this, then this is a 64bits setup.  If not, then you have a 32bits setup.
To check if you have 32-bit or 64-bit Ubuntu, use the command:
```
uname -m
```
If the output is **i686** then you have 32-bit Ubuntu.
If the output is **x86_64** then you have 64-bit Ubuntu.

The Dell version of Ubuntu is 32-bit. Note that it is not *required* to use the Dell-specific Ubuntu if you have Dell hardware. Standard Ubuntu runs just as well on Dell machines. I'm using 64-bit Ubuntu 8.04 on my XPS M1530.

---

### Post by patrickballeux on 2008-10-21
> **jespdj said:**
> To check if you have 32-bit or 64-bit Ubuntu, use the command:
```
uname -m
```
If the output is **i686** then you have 32-bit Ubuntu.
If the output is **x86_64** then you have 64-bit Ubuntu.

The Dell version of Ubuntu is 32-bit. Note that it is not *required* to use the Dell-specific Ubuntu if you have Dell hardware. Standard Ubuntu runs just as well on Dell machines. I'm using 64-bit Ubuntu 8.04 on my XPS M1530.

Thanks, I did't know about this option.

---

