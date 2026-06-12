---
title: "USplash and Menu.lst Problem"
date: 2009-05-26
forum: General Help
---

### Post by PumaSpeedCat on 2009-05-26
I am having a problem, that someone out there may help me with.

When I go to use StartUp Manager to use a usplash theme, and then restart the system, to view it, I end up getting the Error 11 from Grub: Invalid string (or something to that likeness)

So I go back and boot from the Live CD to restore a backup of my menu.lst from menu.lst~ and all works well again.  

I would like to know if there is an easier way to go about doing this (changing themes), so I don't have to do that all the time.

Also how do you turn off "verbose" booting...the check box is not checked for "show text during boot", but yet it still does, or am I reading that option wrong?..

Any ideas/solutions would be of great service and help!

Thank you!

---

### Post by PumaSpeedCat on 2009-05-26
also has anyone tried Splashy?

---

### Post by nebileix on 2009-05-26
Use the command to check for usplash installed in your system.

```
$sudo update-usplash-theme
```

Command to change the theme.

```
 $sudo update-usplash-theme <<your_Theme_name>>
```


To be verbose or not during usplash screen, all depends on the line:

> kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1cc1ed2d-22c2-49a6-8b3a-567732be957c ro [COLOR="Blue"]quiet[/COLOR] splash

Just remove "quiet" if you want text during boot.

---

### Post by PumaSpeedCat on 2009-05-26
I did look in my menu.lst and "quiet" is in the line...so don't know why that does that then...

also Thanks! for the sudo update command... I appreicate it...  it worked!, and I don't mind working in terminal too!!

---

### Post by nebileix on 2009-05-27
How many kernel does ur system have? You may not be booting from the kernel with the "quiet" option on.

Another way is to edit the boot option in grub menu during boot by selecting the kernel to boot and edit the option.

Press 'e' on the highlighted kernel.

Highlight the 'kernel /boot/vmlinuz-2.6.27-7-generic...blah... blah' and press 'e' again.

Look out for the option at the end and make sure the "quiet" option is there.

Once verified, press 'enter' to go back to previous screen and press 'b' to resume boot.

---

### Post by PumaSpeedCat on 2009-05-27
Here is a copy of my menu.lst...as it is...anything above the shown lines, is still set as default, I didn't make any changes to it.

```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		47158fea-77cf-48ab-8b95-1cdf73cd1e12
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=47158fea-77cf-48ab-8b95-1cdf73cd1e12 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		47158fea-77cf-48ab-8b95-1cdf73cd1e12
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=47158fea-77cf-48ab-8b95-1cdf73cd1e12 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		47158fea-77cf-48ab-8b95-1cdf73cd1e12
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1

```

Then sometimes it will not load...unless I restore it again...I still get the Error 11, every so often too

---

### Post by nebileix on 2009-05-27
Sorry I need to verify with u regarding verbose mode boot.

What do you mean by verbose?

1) Only pure black screen without the ubuntu usplash.

2) Or usplash with the textbox enable?

---

### Post by PumaSpeedCat on 2009-05-27
No need to be sorry, 

The screen, when booting, is black screen without a splash, and scrolling text, telling me that each has loaded with an [OK] at the end of each line on the right side of the screen.

also seems now I need to use live CD to copy my menu.lst.backup over to menu.lst then reboot just to boot into Ubuntu.

I have tried using 

sudo grub
find /boot/grub/stage1
--->output is just (hd0,4) 
then when I use
setup (hd0) nothing

---

### Post by PumaSpeedCat on 2009-05-27
Nevermind about that last part about not being able to boot, I fixed grub using SuperGrubDisk.

though everything else above still applies when trying a splas

---

### Post by nebileix on 2009-05-27
What did u do previously b4 the usplash disappear?

Possible cause might be ur /etc/initramfs-tools/conf.d/resume pointing to the wrong swap partition.

Take a look at that.

---

### Post by PumaSpeedCat on 2009-05-28
When I go to that dir, 

```
etc/initramfs-tools/conf.d/resume 
```

there is nothing in there.

Anyway, I appreciate your help greatly!!, but somehow now, I can't boot into linux...I even ran fsck (from root) with -t ext3 /dev/shda5

and it comes back clean, and did the grub thing again...and still cannot boot...so guess I have to re-install Ubuntu, not a biggie though, as I back up stuff all the time...

Anyway... I just wanted to say THANK YOU for your help and patience!, and teaching a nOOb a few things.:D

---

### Post by nebileix on 2009-05-29
You dun need to re-install ubuntu.

The reason usplash not working becuz of that "resume" file missing.

All you need to do is create a empty file and input your swap partition UUID in it.

Like this:

> RESUME=UUID=YourSwapPartitionUUID

Use command:
```
$ sudo blkid
```

To check your UUID.

As for these,

> No need to be sorry,

The screen, when booting, is black screen without a splash, and scrolling text, telling me that each has loaded with an [OK] at the end of each line on the right side of the screen.

also seems now I need to use live CD to copy my menu.lst.backup over to menu.lst then reboot just to boot into Ubuntu.

I have tried using

sudo grub
find /boot/grub/stage1
--->output is just (hd0,4)
then when I use
setup (hd0) nothing

You miss out the step of pointing the root. The process should go like this.

```

$ sudo grub
>find /boot/grub/stage1
>root (hd0,4)
>setup (hd0)
>"Lots of text checking on the files... blah...blah"
>quit

```

If successful, you'll know it from those text.

Try it b4 u re-install.

---

### Post by PumaSpeedCat on 2009-05-29
I re-installed Ubuntu....

even now, when I go into that dir, there is still no file "resume" or any file for that matter,

though the system boots/runs "smooth as butter".

And yes, that was my bad...for not doing the "root (hd0,4)", I realized I kept forgetting it then it hit me.  This did rebuild GRUB, but it didn't want to boot into Ubuntu...but I still could get into Windows.

Again, thank you for being patient with a noob like me!  You and this community are VERY helpful!  BEST TECH SUPPORT I EVER HAD!!!  10/10 stars

---

