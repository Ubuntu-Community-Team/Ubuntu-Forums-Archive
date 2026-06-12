---
title: "Please eject the disc from &quot;TSSTcorp DVD+-RW TS-T633C&quot; manually."
date: 2011-01-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by micael3000 on 2011-01-27
Hello,

Every time I burn a disc Ubuntu doesn't eject it and I can't eject untill reboot.
I do not really know what can cause it.

The message shown:
> Please eject the disc from "TSSTcorp DVD+-RW TS-T633C" manually.
The disc could not be ejected though it needs to be removed for the current operation to continue.


Ubuntu 10.10;
DELL Studio 1450.

Can anyone help me to figure out what is wrong?

Thanks in advance

---

### Post by noisygecko on 2011-03-02
This same thing happens with me with Ubuntu 10.10 on an AMD64 machine:

    Please eject the disc from "ASUS DRW-24B1ST   a" manually.

The first CD I wrote had errors.  I was hoping this second one wouldn't have errors, but it did.

I hate CDRs.  They constantly have errors and don't work since the first ones I was trying to write back when 2x speed was amazing.  Such a stupid waste of time.

---

### Post by sidzen on 2011-03-02
download and install wodim
[PHP]sudo apt-get -f install wodim[/PHP]
then test your devices 

xxxxx@mustangjoe-desktop ~ $ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'    rwrw-- : 'HL-DT-ST' 'BD-RE  UH10LS20'
-------------------------------------------------------------------------
xxxxx@mustangjoe-desktop ~ $ wodim dev=/dev/scd0 -sao -eject speed=8 absolute/path/to/filename.iso

wodim is much more reliable than that (blank) *brasero*!

---

### Post by micael3000 on 2011-03-04
It works!

However, is there no way to 'fix' it? I mean, so I don't have to type this command everytime I write a disc...

Thanks

---

### Post by sidzen on 2011-03-10
> **micael3000 said:**
> It works!

However, is there no way to 'fix' it? I mean, so I don't have to type this command everytime I write a disc...

Thanks
Fixit?  Brasero?  I get rid of it
[PHP]sudo apt-get remove brasero[/PHP] then add K3b
[PHP]sudo apt-get -f install k3b[/PHP]then reboot 
[PHP]sudo init 6[/PHP] and make sure k3b is functional.

It's much better than brasero.
(another is xfburn)

BTW -- you're welcome.  Enjoy!

---

### Post by tushar maroo on 2011-03-10
bassically what is your problem??if it is occuring due to not working of inbuilt function key of the laptop,then create a new key combination for ejection of cd........Simply go to System \ Preferences \ Keyboard Shortcuts and then assign a hotkey to the Sound \ Eject item.

---

### Post by micael3000 on 2011-05-06
Problem solved. (k3b is indeed way better)
Also, the script to eject is working greatly.

---

### Post by tgwaste on 2012-05-05
Using an alternate program is _not_ a solution to this problem.

This needs to be fixed and work properly with the software that comes with Ubuntu.

---

