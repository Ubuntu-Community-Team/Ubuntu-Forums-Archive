---
title: "Encyption for usb sticks?"
date: 2007-05-09
forum: Desktop Environments
---

### Post by asearle on 2007-05-09
I have a usb stick that I carry with me and which contains data that I would like to encrypt to protect in case of loss.

There seem to be a number of (Windows?) encryption programs around so I was wondering if Linux/Ubuntu can read/write to these sticks using the same encryption mechanism?  I hope this is the case as this would allow me to continue to use a single stick from both the Windows and the Linux environments.

Maybe someone could recommend a particularly good encryption program/mechanism that I could use?

Many thanks for your help.

Cheers,
Alan Searle

---

### Post by mve-lamb on 2007-05-09
Hi!
you can try this one: [TrueCrypt 4.3a]("http://www.truecrypt.org/downloads.php")
it's good program with number of encription methods, i've use it when i was windows user :confused: 
I'll try it on Ubuntu 7.04 now....

---

### Post by potterzot on 2007-08-03
I had a similar desire.  I have a usb stick with sensitive info that needs to be encrypted, but at the same time can't guarantee that each computer I use it on will have truecrypt on it.  I used the guide here:[http://www.juand.ca/how-to-secure-your-usb-thumbdrive/]("http://www.juand.ca/how-to-secure-your-usb-thumbdrive/")  to get a file set up on my usb stick and so that I can use it on any windows machine.  Then in my linux machine i installed truecrypt, and wrote the following script:

```

#!/bin/bash

echo;

case "$1" in
    "") echo "Usage: ${0##*/}"; exit $E_PARAM;;
    -m) echo "Mounting the truecrypt volume..."; truecrypt -u /media/POTTERZOT/tcfolder /home/potterzot/Desktop/secure-usb;;
    -u) echo "Unmounting the truecrypt volume"; truecrypt -d;;
esac
```

Then I just do

```
secure-usb -m
```

to mount, and 

```
secure-usb -u
```

to unmount

---

