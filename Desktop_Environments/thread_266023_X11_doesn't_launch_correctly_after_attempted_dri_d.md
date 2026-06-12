---
title: "X11 doesn't launch correctly after attempted dri driver update -- can no longer boot"
date: 2006-09-26
forum: Desktop Environments
---

### Post by ropers on 2006-09-26
Hi,this time I really need help:

I have SiS 630 onboard graphics hardware and tried to install DRI drivers. 
I ran across these instructions:

[http://www.ubuntuforums.org/showthread.php?t=32043](http://www.ubuntuforums.org/showthread.php?t=32043)

I adapted them to sis and essentially did what's explained in the first three posts.

Now Ubuntu Dapper 6.06 LTS won't fully boot anymore -- while I can load the recovery console, when trying to load the X11/GNOME/gdm logon, the screen goes blank except for some "garbage pixels" at the top and even Ctrl-Alt-F1 doesn't restore the display to something that's human-digestible. 

I ran both the installer scripts, the 
http://dri.freedesktop.org/snapshots/common-<something>
and the 
http://dri.freedesktop.org/snapshots/sis-<something>

(most recent versions).

For now I'm no longer fussed about DRI -- I just need a quick way to repair my installation so I can get back to my Ubuntu desktop.
I am posting this while booted into the install CD. 

Any help VERY much appreciated! :)

--ropers

---

### Post by dwasifar on 2006-09-26
> **ropers said:**
> Hi,this time I really need help:

I have SiS 630 onboard graphics hardware and tried to install DRI drivers. 

Now Ubuntu Dapper 6.06 LTS won't fully boot anymore -- while I can load the recovery console, when trying to load the X11/GNOME/gdm logon, the screen goes blank except for some "garbage pixels" at the top and even Ctrl-Alt-F1 doesn't restore the display to something that's human-digestible. 

Possibly your xorg.conf is munged up?  If the driver installation backed up your xorg.conf - and often they do - try restoring it.  (Apologies in advance if the following is too basic.)

Create a mount point and mount your hard drive from the live cd:

[COLOR="RoyalBlue"]  sudo -s
  mkdir /mnt/root
  mount -t ext3 /dev/hda1 /mnt/root[/COLOR]

Switch to the X11 directory and list the files:

[COLOR="RoyalBlue"]  cd /mnt/root/etc/X11
  ls -l[/COLOR]

If you see a backup xorg.conf, restore it:

[COLOR="RoyalBlue"]  cp xorg.conf_backup_200609252233 xorg.conf[/COLOR]

Then reboot. 

Hope this helps.

---

### Post by ropers on 2006-09-27
Thanks for your reply! :)

Sadly it didn't get me far yet:

I don't seem to have a backed up version of xorg.conf:

```
root@ubuntu:/mnt/root/etc/X11# ls -al
total 84
drwxr-xr-x  10 root root  4096 2006-09-22 19:16 .
drwxr-xr-x 109 root root  4096 2006-09-26 21:50 ..
drwxr-xr-x   2 root root  4096 2006-08-05 23:31 app-defaults
drwxr-xr-x   3 root root  4096 2006-08-05 23:21 config
drwxr-xr-x   2 root root  4096 2006-08-05 23:25 cursors
-rw-r--r--   1 root root    14 2006-08-05 23:32 default-display-manager
drwxr-xr-x   6 root root  4096 2006-08-05 23:20 fonts
lrwxrwxrwx   1 root root     6 2006-09-12 02:12 gdm -> ../gdm
-rw-r--r--   1 root root 17371 2005-12-22 01:00 rgb.txt
lrwxrwxrwx   1 root root    13 2006-09-12 02:12 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 2006-08-05 23:24 xinit
drwxr-xr-x  10 root root  4096 2006-08-05 23:23 xkb
-rw-r--r--   1 root root  4450 2006-09-22 10:12 xorg.conf
drwxr-xr-x   2 root root  4096 2006-05-28 19:35 Xresources
-rwxr-xr-x   1 root root  3911 2006-03-20 12:29 Xsession
drwxr-xr-x   2 root root  4096 2006-08-05 23:32 Xsession.d
-rw-r--r--   1 root root   234 2006-03-20 12:29 Xsession.options
-rw-------   1 root root   614 2006-08-05 23:20 Xwrapper.config
root@ubuntu:/mnt/root/etc/X11#

```

but I found this in my dmesg:

```

[17179682.068000] pcc_acpi: loading...
[17179694.708000] [drm] Initialized drm 1.0.1 20051102
**[17179694.900000] **** SET: Misaligned resource pointer: cfb1b5a2 Type 07 Len 0**
[17179694.900000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 3
[17179694.900000] PCI: setting IRQ 3 as level-triggered
[17179694.900000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 3 (level, low) -> IRQ 3
[17179694.900000] [drm] Initialized sis 1.1.0 20030826 on minor 0
[17179694.916000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179694.916000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179694.916000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179697.552000] lp0: using parport0 (interrupt-driven).
```

---

### Post by dwasifar on 2006-09-27
Yipes.

You can boot to the command line, right?  Try running [COLOR="RoyalBlue"]sudo dpkg-reconfigure xserver-xorg[/COLOR].  It'll walk you through your xorg setup.

I suspect you're eventually going to have use [COLOR="RoyalBlue"]sudo apt-get remove[/COLOR] to uninstall the DRI drivers.

---

### Post by ropers on 2006-09-27
dwasifar: Many thanks for your help! :) -- though I have to admit that I broke down and just reinstalled in between time. I did still have another FAT32 hard drive attached, so I booted from the install CD, mounted both the broken install partition and the FAT32 one, backed up what I wanted to keep onto that and then wiped the Ubuntu hard drive. Your previous message was helpful to that end. I do regret doing that somewhat, because I guess I could have learned more by actually fixing the problem instead of just reinstalling, but there you go, I was just too impatient.

Again, many thanks for your help! :)


PS: For the benefit of future readers of this thread -- this is roughly what I did once booted into the install CD.
1. Configured the network via System -- Administration -- Networking.
(This is not required if you use DHCP. Also you will need to know your details if you don't.)
2. Application -- Accessories -- Terminal:
sudo -s
mkdir /mnt/root
mkdir /mnt/fattie
mount /dev/hda1 /mnt/root
mount -t vfat -o rw /dev/hdc1 /mnt/fattie
cd /mnt/root/home/myusername/Desktop
cp -r * /mnt/fattie/

---

### Post by dwasifar on 2006-09-28
Hey, I'm just glad to be any help at all.  Mostly I *ask* for help here.  :)  But I had just gone the full route with video drivers, screwed-up xconf files, and recovering from a live CD, and your problem seemed familiar.

Off the topic - I took a look at your reading list.  If you liked Burgess' "A Clockwork Orange" you would probably also like his "The Wanting Seed," not as well known but written around the same time.  Keep an eye out for it if you get the chance.

---

### Post by ropers on 2006-09-28
> **dwasifar said:**
> 
Off the topic - I took a look at your reading list.  If you liked Burgess' "A Clockwork Orange" you would probably also like his "The Wanting Seed," not as well known but written around the same time.  Keep an eye out for it if you get the chance.

Hey thanks. :) I'll do that.

---

