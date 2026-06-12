---
title: "Royally messed up my GRUB..."
date: 2009-05-04
forum: General Help
---

### Post by xi_Slick_ix on 2009-05-04
So, just finished installing Windows XP on my desktop.  I have 8.04 as my main install, and it was there prior to Windows.  Of course when you install Windows it does a wonderful job at wiping out the boot loader.  To fix this I followed this guide:

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

Which just happened to have all of the hard drive locations exactly as I have them for my various partitions.  I placed Windows in the boot menu as so:

```
title   Windows 95/98/NT/2000
root   (hd0,3)
makeactive
chainloader   +1
```

And when I placed it in the boot menu, it I placed it at the top of the list.  The result:  Grub starts to load and then immediately boots to XP.

So now I need to know my next step.  I tried going back to the live CD and telling the 1st set of commands from the guide above, but it still loaded directly into XP.

Any suggestions? And can I edit my boot menu from a Live CD?

---

### Post by zvacet on 2009-05-04
Yes,you can edit your menu list from live CD.

```
gksudo gedit /boot/grub/menu.lst
```

and add this after last Ubuntu line 

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS

title   Windows 95/98/NT/2000
root   (hd0,3)
makeactive
chainloader   +1


Of course you will remove previous entry for windows from your menu list.Save and close.You should be good.

---

### Post by xi_Slick_ix on 2009-05-04
And my fears worsen, the boot menu in gedit it utterly blank.  I would assume its safe to say I have a problem

---

### Post by xi_Slick_ix on 2009-05-04
```
ubuntu@ubuntu:~$ gksudo gedit /boot/grub/menu.lst

** (gedit:7730): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.RN8DTU': No such file or directory

I/O error : No such file or directory
I/O error : No such file or directory
```

---

### Post by xi_Slick_ix on 2009-05-04
Actually for the sake of speed I'll probably just reinstall it - I keep all my media on a separate partition.  It will end up being the same amount of time and effort

---

### Post by caljohnsmith on 2009-05-04
You've probably all ready reinstalled I would imagine, but just for future reference, if you want to modify your Grub's menu.lst from the Live CD, you first have to mount your Ubuntu partition. In other words, when you did:
```
gksudo gedit /boot/grub/menu.lst
```
That tries to pull up the menu.lst from the Live CD's /boot/grub directory, but that file does not exist on the Live CD. You instead have to mount your Ubuntu partition and then access the menu.lst like:
```
sudo mount /dev/[COLOR="Red"]sdaX[/COLOR] /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
Replace sdaX with your Ubuntu partition, and then you should be able to pull up its menu.lst in gedit. Anyway, hope you got your problem sorted out.

Cheers,
John

---

