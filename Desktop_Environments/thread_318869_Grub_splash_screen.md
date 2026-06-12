---
title: "Grub splash screen"
date: 2006-12-14
forum: Desktop Environments
---

### Post by juantovarm on 2006-12-14
I have just installed kde desktop on my ubuntu 6.10. I  prefer the ubuntu grub splash screen than the kubuntu one. Does anyone know how to change this?

Thanks

---

### Post by ZERO_SHIFT on 2006-12-15
Check this link :

[http://art.gnome.org/themes/splash_screens/](http://art.gnome.org/themes/splash_screens/)

---

### Post by paparucino on 2006-12-15
> **juantovarm said:**
> I have just installed kde desktop on my ubuntu 6.10. I  prefer the ubuntu grub splash screen than the kubuntu one. Does anyone know how to change this?

Thanks
Check this: in /etc/alternatives/ you should have a simlink called @usplash-artwork.so.
In your case this link point to /usr/lib/usplash/usplash-theme.kubuntu.so.
Change the above link so to point to /usr/lib/usplash/usplash-theme.ubuntu.so.

Hope it helps

---

### Post by Aggienator on 2007-01-27
> **paparucino said:**
> Check this: in /etc/alternatives/ you should have a simlink called @usplash-artwork.so.
In your case this link point to /usr/lib/usplash/usplash-theme.kubuntu.so.
Change the above link so to point to /usr/lib/usplash/usplash-theme.ubuntu.so.

Hope it helps

Sorry to be dim, how do I change the link. I've found it wityh nautilus, but I can't change  the link in properties. Presumably I need to do something command line in terminal? :confused:

---

### Post by JamieC on 2007-01-27
Post the output of the following commands (to be run in terminal):
```

sudo cp /usr/lib/usplash/usplash-default.so /usr/lib/usplash/usplash-artwork.so
sudo dpkg-reconfigure linux-image-`uname -r`

```

---

### Post by Aggienator on 2007-01-27
```
geoff@ubuntu-server:~$ sudo cp /usr/lib/usplash/usplash-default.so /usr/lib/usplash/usplash-artwork.so
Password:
cp: cannot stat `/usr/lib/usplash/usplash-default.so': No such file or directory
geoff@ubuntu-server:~$
```
```

geoff@ubuntu-server:~$ sudo dpkg-reconfigure linux-image-`uname -r`
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.17-10-server
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.17.1-10.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.17.1-10.34 was configured last, according to dpkg)
Running postinst hook /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-10-server
Found kernel: /boot/vmlinuz-2.6.15-27-server
Found kernel: /boot/vmlinuz-2.6.15-26-server
Found kernel: /boot/vmlinuz-2.6.15-23-server
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

geoff@ubuntu-server:~$ 
```


Does this help?

---

### Post by JamieC on 2007-01-27
Hm, it can't find the splash image, post the output of the following:
```

sudo cp /usr/lib/usplash/usplash-theme-ubuntu.so /usr/lib/usplash/usplash-artwork.so
sudo dpkg-reconfigure linux-image-`uname -r`

```

---

### Post by Aggienator on 2007-01-27
```
geoff@ubuntu-server:~$ sudo cp /usr/lib/usplash/usplash-theme-ubuntu.so /usr/lib/usplash/usplash-artwork.so
cp: `/usr/lib/usplash/usplash-theme-ubuntu.so' and `/usr/lib/usplash/usplash-artwork.so' are the same file
geoff@ubuntu-server:~$ sudo dpkg-reconfigure linux-image-`uname -r`
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.17-10-server
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.17.1-10.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.17.1-10.34 was configured last, according to dpkg)
Running postinst hook /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-10-server
Found kernel: /boot/vmlinuz-2.6.15-27-server
Found kernel: /boot/vmlinuz-2.6.15-26-server
Found kernel: /boot/vmlinuz-2.6.15-23-server
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
```

?

---

### Post by JamieC on 2007-01-27
Try restarting to see if it has had any effect?

---

### Post by Aggienator on 2007-01-27
> **JamieC said:**
> Try restarting to see if it has had any effect?

Thanks Jamie, I'll do that and then off to bed I think (11pm here)

Aggie

---

### Post by paparucino on 2007-01-27
> **Aggienator said:**
> Sorry to be dim, how do I change the link. I've found it wityh nautilus, but I can't change  the link in properties. Presumably I need to do something command line in terminal? :confused:
Run a terminal, then
```

sudo rm /etc/alternatives/usplash-artwork.so

```

Next step
```

sudo ln -s /usr/lib/usplash/usplash-theme-ubuntu.so     /etc/alternatives/usplash-artwork.so

```

If you don't get any error, may be your is correct :-)
Let me know.

---

### Post by Aggienator on 2007-01-27
Thanks Guys, I've got it back!

Cheers Aggie

---

### Post by JamieC on 2007-01-27
> **Aggienator said:**
> Thanks Guys, I've got it back!

Cheers Aggie

You're welcome! 

11pm there? Hm, you're thirty minutes behind. Haha, just kidding.

---

### Post by Aggienator on 2007-01-27
> **JamieC said:**
> You're welcome! 

11pm there? Hm, you're thirty minutes behind. Haha, just kidding.

Hey, thats the closest to now I've ever been!

---

### Post by jerrylamos on 2007-01-30
Entry #5 above, Magic!  

I'm running Edgy Eft Christmas 2006 edition.  On DVD, there's a nice splash screen, with light red text on a dark red background, whirling Ubuntu symbol, looks impressive.

When installed it reverts to the usual Edgy Eft splash, very tiny print dark blue on black just about illegible.

Ran your two command lines, which complained "none found", then on restart magically got the very handsome DVD splash screen!

Thanks much!  Now of course I've got to go straighten out menu.lst, since there's Win98 (for printer head clean & cartridge change), Dapper, Edgy, and Xubuntu on it.

Thanks Again!

---

