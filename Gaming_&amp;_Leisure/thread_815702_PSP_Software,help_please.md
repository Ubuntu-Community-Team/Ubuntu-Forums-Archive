---
title: "PSP Software,help please"
date: 2008-06-01
forum: Gaming &amp; Leisure
---

### Post by Dark Aspect on 2008-06-01
Hello

I have tried to install both PSPVC and QPSPmanger on Ubuntu 8.04 to convert video files to my PSP but neither work.PSPVC fails to compile and QPSPmanger works but fails to convert any of my video files.Is there any up-to-date how to for either PSPVC/QPSPmanger or is there some equivalent windows software that works good enough on wine to buy?

---

### Post by Dark Aspect on 2008-06-03
BUMP

I would really like to use my PSP to watch movies on the go.

---

### Post by AJB2K3 on 2008-06-04
I've haven't found anything yet.

---

### Post by CronoDekar on 2008-06-04
I've been able to get this to work to install PSPVC (mainly, making sure to install the dependencies listed):

[http://ubuntuforums.org/showpost.php?p=2258647&postcount=5](http://ubuntuforums.org/showpost.php?p=2258647&postcount=5)

---

### Post by Dark Aspect on 2008-06-05
> **CronoDekar said:**
> I've been able to get this to work to install PSPVC (mainly, making sure to install the dependencies listed):

[http://ubuntuforums.org/showpost.php?p=2258647&postcount=5](http://ubuntuforums.org/showpost.php?p=2258647&postcount=5)

```
yasm -f elf -m amd64 -Icommon/amd64 -o common/amd64/dct-a.o common/amd64/dct-a.asm
make: yasm: Command not found
make: *** [common/amd64/dct-a.o] Error 127
-e \E[01;31mERROR during compilation or installation of X264
```

Might have been helpful to mention I am using a 64-bit operating system.If PSPVC compiled for you this way on hardy and your using x86,then it might not be 64-bit compatible.

---

### Post by dudeofthedead on 2008-06-05
If 64-bit...

```
apt-get install ia32-libs
``` // ia32-libs may be called something else on your machine...

---

### Post by CronoDekar on 2008-06-05
Maybe you have to install yasm too?  I didn't have to -- not really sure why.  Unless it just depends on which version you're installing,

---

### Post by Dark Aspect on 2008-06-05
> **CronoDekar said:**
> Maybe you have to install yasm too?  I didn't have to -- not really sure why.  Unless it just depends on which version you're installing,

Thank You,that did it.

```
-e \E[01;32mPSPVC installation completed

```

---

### Post by frodon on 2008-06-06
The easiest way i know is just to use avidemux (in the repositories), in the auto Tab choose PSP format then click convert, that's all.

This works like a charmon my PSP.

---

### Post by meer_mortal on 2008-06-26
Download PSPVC. Extract.
In Terminal "sudo apt-get install nasm libfaac-dev libxvidcore-dev libgtk2.0-dev liba52-dev "
Let packages install then sudo ./install.sh .

Stolen from [https://help.ubuntu.com/community/PSP](https://help.ubuntu.com/community/PSP)

---------------------------------------------------------
Ubuntu8.04 rules my desktop!!!

---

