---
title: "Grub booting XP - 3OS (Vista, XP and U81)"
date: 2008-12-11
forum: General Help
---

### Post by Grunzi on 2008-12-11
Dear forum,

I'm pretty new to linux but after I played around with a live system, I decided to install it.
Now I have the following problem that I'm not able to solve:
I have the following system setup:
sda1: Vista (active) ("working" system) "C:\"
sdb1: Windows XP (for playing games ^^) "D:\" (active)
sdb2: Linux Swap
sdb3: /
sdb4: /home

Grub works fine starting both Ubutu and Vista - but fails to start XP. Workaround would be to start XP via Vista Bootmanager, but I hate to step through an boot "hierachy". 

I played with several entries e.g. root (1,0), root noverify(1,0) in grub and also several setting (rdisk, partition) in boot.ini (from D:\).

Therefore my questions: How do I enable XP from the second harddisk to start up ?

Thanks in advance! ):P

Grunzi

---

### Post by caljohnsmith on 2008-12-11
It is likely that either Vista has its boot files in your Windows XP partition, or Windows XP has its boot files in your Vista partition, unless you disconnected one of the drives when installing either XP/Vista; if you want to boot them separately, you might need to separate their boot files, possibly reconfigure boot.ini/BCD, and maybe fix the boot sector of one of the partitions. It's not too big of a deal, but it could take some work. If you want to do that, how about downloading the attached "info_script.sh.txt" to your desktop, and do the following in a terminal (Applications > Accessories > Terminal):
```
sudo sh ~/Desktop/info_script.sh.txt
```
And post the output. We can work from there if you want. :)

---

### Post by thegizmoguy on 2008-12-11
I belive the only way to dual boot XP-Vista-Ubuntu (what i'm doing) is to have Vista control the XP boot and Grub to control Vista.  To get XP back in Vista's boot menu, use EasyBCD, add a new OS entry.  Find whatever partition has "ntldr" in it and use that.  Then there should be a boot.ini in that same partition.  Mine looks like this (this is XP's boot.ini).  Basically Vista loads up ntldr which is officially XP and then XP loads up boot.ini:

[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer

Note you may have to do trial and error for where to place/find ntldr and which partition your XP install is on.

---

### Post by Grunzi on 2008-12-11
Hi,

thanks for your answer - in fact I currently do it like this (I used bcdedit or so - nice piece of sw :-( )
But I'd like to have grub to startup XP as well. 
Minor thing, but nice to have :-)

---

### Post by Grunzi on 2008-12-11
It is likely that either Vista has its boot files in your Windows XP partition, or Windows XP has its boot files in your Vista partition, unless you disconnected one of the drives when installing either XP/Vista; if you want to boot them separately, you might need to separate their boot files, possibly reconfigure boot.ini/BCD, and maybe fix the boot sector of one of the partitions. 
I copied XP startup files (ntldr,...) to sda1 and used bcdedit to bring XP from vista boot loader up. This works fine (..now :-)
I copied the same set of files to sdb started xp in rescue mode from cd and did a "fixboot d:". In addition I set the bootflag via fdisk /dev/sdb to sdb1.
I'm currently in the office, I post the output from your script later today. 
A BIG THANK YOU IN ADVANCE!

---

### Post by Grunzi on 2008-12-11
Hi caljohnsmith,

attached the requested output - hope you can help.

Thanks in advance :p

Grunzi

---

### Post by caljohnsmith on 2008-12-11
Grunzi, that's great, it looks like you have almost everything configured to boot XP from its own partition all ready; you do need to change your XP entry in the menu.lst though, so how about first opening your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And then replace your XP entry at the bottom of the file with:
```
title       Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Reboot, select XP from the Grub menu, and let me know exactly what happens. We can work from there. :)

---

### Post by Grunzi on 2008-12-11
Hi caljohnsmith,

what should I say: IT WORKS.

Thanks so much for support

Kind regards from cold germany to sunny(?) california.

Grunzi

---

### Post by caljohnsmith on 2008-12-11
That's great news, I'm glad it turned out to be an easy fix; cheers and have fun with Vista, XP, and Ubuntu. :)

---

### Post by TurambarTurin on 2009-09-02
Can somebody explain it more clearly? I have Ubuntu/Vista/XP. How can I boot XP from grub?

My output is in attachment. I would be glad if you can help

---

### Post by egalvan on 2009-09-02
This is an old thread, and that is an out-dated script.

Use caljohnsmith's latest, located here.

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

then upload the results again.

---

### Post by epicoder on 2009-09-02
Run this script as root in a terminal. Somewhere in the output will be something(s) in this form: (hd0,x)

Copy the (hd0,x) with the largest x and type 'sudo gedit /boot/grub/menu.lst'.

Add these lines to the end of the file:
```
title Whatever you want here
    root [paste here]
    makeactive
    chainloader +1
```Indentation should be 8 spaces, but it's not crucial.

---

