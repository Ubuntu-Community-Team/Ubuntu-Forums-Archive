---
title: "windows wont boot!"
date: 2006-04-01
forum: Desktop Environments
---

### Post by sharperguy on 2006-04-01
Help!

Only thing that has changed is that i installed anotheer version of ubuntu on a different partition to my main one (long story) and that was the only thing i can think of that has changed since my last windows boot. (actually i was boot windows fine before after doing this, the i removed the partition i was booting from thinking i had sorted grub to boot from my main partition, but it didnt want to know and wouldnt boot so i reinstalled ubuntu again and now windows wont boot.)

ahhh

Hellp

please

...

---

### Post by souki on 2006-04-01
can you boot ubuntu ?
from ubuntu can you see your windows partition ?
what is you windows version ?
what is your ubuntu version ?
can you post here your /boot/grub/menu.lst ?

---

### Post by sharperguy on 2006-04-01
Ubuntu = Breezy, will boot (both installs) (main on /dev/hdb3, temp on /dev/hdb8 )

Windows = XP, parition shows fine (hda1)

Menu.lst :
Modified to remove unececary (i hope) option to boot to the new ubuntu install so i dont have to select my main one every time
```


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb3.
title		Ubuntu, kernel 2.6.12-10-386 
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb3 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb3.
title		Ubuntu, kernel 2.6.12-10-386 (recovery mode) 
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb3 ro single 
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb3.
title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb3 ro quiet splash 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb3.
title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb3 ro single 
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb3.
title		Ubuntu, memtest86+ 
root		(hd1,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		linux (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz root=/dev/hdb1 splash=silent 
initrd		/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		linux-nonfb (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz root=/dev/hdb1 splash=silent 
initrd		/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		failsafe (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz root=/dev/hdb1 failsafe splash=silent 
initrd		/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by souki on 2006-04-01
I see nothing wrong in your menu.lst

do you have several windows partitions ?
how many partitions on /dev/hda ? how big ?

if the hda1 partition is outside of the area that grub can read, you have to use rootnoverify
```
title WindowsXP
rootnoverify (hd0,0)
makeactive
chainloader +1
```

if you have several windows partition (primary) you have to hide them with hide(x,y)

```
title WindowsXP
unhide (hd0,0)
hide (hd0,1)
rootnoverify (hd0,0)
makeactive
chainloader +1
```

---

### Post by sharperguy on 2006-04-02
i just have one big partition on the windows drive. (hda1)

---

### Post by souki on 2006-04-03
[QUOTE=sharperguy]i just have one big partition on the windows drive. (hda1)[/QUOTE]
I'm not sure but you should try the 'rootnoverify' option
it won't be dangerous for your data

---

### Post by sharperguy on 2006-04-04
thanks, I will try that now

---

### Post by Hairy_Palms on 2006-04-04
can you mount the drive under linux to verify that its all fine, 
make a folder in home called windows and use a command like this
sudo mount -t /dev/hda1 /home/sharperguy/windows
if all your data is there then you could try fixing grub by reinstalling from the ubuntu cd instructions are 
[http://www.ubuntuforums.org/showthread.php?t=24113](http://www.ubuntuforums.org/showthread.php?t=24113)

---

### Post by sharperguy on 2006-04-05
Yea, it auto-mounts fine on ubuntu and i can acess all the files fine.

Its just when I try to boot it will only get to "Beggining part 2" (or something) and then goes back to the selection screen.

Most of my data is on ubuntu but i still need windows for a couple of things. I intalled linux on this box pretty much a soon as i got it. Still got a few major programs on windows that i need.

---

### Post by sharperguy on 2006-04-11
I have also tryed reinstalling ubuntu.

I think i know what the problem is and how it was caused!!!:

I have run the following commands in grub from my main ubuntu partition (hdb3)

```

root (hd1,2)  //this bits ok

setup (hd0,0) //this is not

```

i assume it overwrote the windows boot information, so when i try to boot windows it takes me to hdb3's menu.lst, that also solves my problem of having to have a second install of ubuntu at all!

What I should have done was:

root (hd1,2)

setup (hd1,2)

If this is not correct either please tell me before i mess things up even more.


Anyway, I still dont have the solution, and I need it soon. How do I get the boot information back onto hda1?

---

### Post by GatorV on 2006-04-11
Well I think the easiest way will be to use the XP CD, use fixmbr, or fixboot, then boot to Ubuntu with the setup CD, and reinstall grub...

---

### Post by lucky2 on 2006-04-11
Do you have, the original Windows CD?
Do you have, the emergency repair disks (2) that were made while installing XP?
Do you have, a simple boot disk (floppy with NTLDR, Boot.ini, Ntdetect.com)?

---

### Post by lucky2 on 2006-04-11
Didn't see you post GatorV, It makes sense.

---

### Post by sharperguy on 2006-04-11
Afaid i dont have any of those things....

Is there somewhere i can donwload an xp boot disk?

EDIT: found this page which has a solution to the problem:[http://www.jalug.org/learning/bootsectorswinxplinux]("http://www.jalug.org/learning/bootsectorswinxplinux")

However you still need the XP installation CD, which i dont have.

There is the chance that I could borrow one, however would it work if it was not the one I originaly installed XP with (ie it has a different registration code).

---

### Post by Neky on 2006-04-11
Use whatever XP CD you have, all you need from any of them is Recovery Console. Boot properly, like you wan`t to install XP and at some time you will get  the option to "press R for Recovery Console". Do that. Note that you will need a "administrator password" which was set at an earlier installation of XP. When you access the RC ( Recovery Console ) type :

1                               // to choose Win XP
*administrator password*               // ENTER if none
fixmbr                           // to write original Master Boot Record to HDD
confirm it.


Sorry for my bad english, I hope you undestood my explanation.

---

### Post by sharperguy on 2006-04-12
hmm

Well i've fixed various problems on my computer but windows still wont boot, not it goes:

Grub boots, i selects windows, the computer restarts.

I used, fixboot and fixmbr and other combinations and this is the best i could get. (i had to reinstall grub with the live-cd a few times)

---

