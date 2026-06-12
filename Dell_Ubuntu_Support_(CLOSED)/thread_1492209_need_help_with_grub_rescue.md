---
title: "need help with grub rescue"
date: 2010-05-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yashdosi on 2010-05-24
Hii...
can any1 tell me what to do .....
i tried to upgrade my ubuntu to the latest version 10.04 using the update manager
everything worked fine till grub installation started ...
it told me to select some devices..
there was a help link it said you can select all the devices if you are unsure which one to select ....so i selected all of then and clicked forward ....but it said installation failed ..then i selected 
sda2 or maybe sda1
and continued with the installation...
then i had to reboot my pc and when i rebooted my pc ....it simply opened 
the grub rescue prompt....
now i simply dont know what to do....:confused:

---

### Post by drs305 on 2010-05-24
yashdosi, welcome to the Ubuntu forums. :-)

Here is a link to the community doc which details how to boot from the recovery mode.
[https://help.ubuntu.com/community/Grub2#Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Rescue%20Mode")

Above the section linked are other ways of booting from a Grub command line. 

Another option is to boot the LiveCD and reinstalling Grub2. There are instructions in the doc for that as well.

The recommended procedure is to install Grub2 to a *drive* and not to a specific partition.

If you need further help just give us the details. Running and posting the results of this script from the LiveCD will be helpful if you need more assistance.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by yashdosi on 2010-05-25
> **drs305 said:**
> yashdosi, welcome to the Ubuntu forums. :-)

Here is a link to the community doc which details how to boot from the recovery mode.
[https://help.ubuntu.com/community/Grub2#Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Rescue%20Mode")

Above the section linked are other ways of booting from a Grub command line. 

Another option is to boot the LiveCD and reinstalling Grub2. There are instructions in the doc for that as well.

The recommended procedure is to install Grub2 to a *drive* and not to a specific partition.

If you need further help just give us the details. Running and posting the results of this script from the LiveCD will be helpful if you need more assistance.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")
1. **ls**  
    2. **set  prefix=(hdX,Y)/boot/grub**  
    3**set root=(loop0)** 
    4. **set**  
    5. **ls  /boot**


**i did this much then an error came up saying**
**error: no such disk**
[B]onw i m again stuck
[/B]

---

### Post by wilee-nilee on 2010-05-25
Since we don't know if youir dual booting or anything really post this script in code tags.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by yashdosi on 2010-05-25
yes i m dual booting...
i hv installed windows 7 as my primary operating system..
and i installed ubuntu within it...
but now i cnt open any1 of them...

---

### Post by yashdosi on 2010-05-25
can u please tell me step by step what to do with this boot info script...since i m very new to these things i m not getting anything...
is there anyway in which the reinstallation dvd of windows 7 can help??
i dnt hv any cd or dvd of ubuntu... :-(

---

### Post by wilee-nilee on 2010-05-25
n

---

### Post by wilee-nilee on 2010-05-25
This is beyond me, I am not sure what has happened I am not familiar with wubi installs.

---

### Post by bcbc on 2010-05-25
So you installed the grub to the MBR and all partitions? If you were running ubuntu installed within windows (i.e. using wubi) then you need to get the windows bootloader back on the MBR of your drive.

But you'll still have issues as the bootsector will also have been damaged, so you need to recover this.

It's possible to do this with the windows dvd the commands are ```
bootrec /fixmbr
bootrec /fixboot
```

The bootinfoscript is really useful, but if you can't get hold of an ubuntu boot cd, then you'll have to use the windows repair option.

Here's a microsoft link for more info: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by yashdosi on 2010-05-26
thnx a lot ......it worked..!!

---

### Post by bcbc on 2010-05-26
Great news :)

---

