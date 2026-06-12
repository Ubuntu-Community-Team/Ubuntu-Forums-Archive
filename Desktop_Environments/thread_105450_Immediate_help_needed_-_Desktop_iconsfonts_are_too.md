---
title: "Immediate help needed - Desktop icons/fonts are too big"
date: 2005-12-18
forum: Desktop Environments
---

### Post by Redindian on 2005-12-18
Suddenly my desktop icons and fonts are appearing too big starting from the login screen. I dont know where to start....help me.
Thanks.

---

### Post by Redindian on 2005-12-18
BTW....my screens are also too big. I coudn't able to see the full window of my browser. 

Helloooooo......anyone out there to help me?????????

---

### Post by aysiu on 2005-12-18
Try this: ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo nano /boot/grub/menu.lst
``` Find the entry you usually boot from. Mine looks like this ```
title           Ubuntu Linux
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda6 ro quiet
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot
``` Add vga=791 in the kernel line. So if I did that on mine, it would now look like this ```
title           Ubuntu Linux
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda6 ro quiet vga=791
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot
``` Save (control-x), confirm (y), exit (Enter) and reboot.

---

### Post by Redindian on 2005-12-18
aysiu,
THanks and it didn't work. It only reduced my startup script font very small, after that my login screen back to big fonts. When i login gnome, i'm getting big fonts, icons, windows are too big to see....i don't know what went wrong.

---

### Post by aysiu on 2005-12-18
Maybe you need to do Control-Alt-F1 and ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Redindian on 2005-12-18
BTW..here's the creenshot of my desktop.

---

### Post by aysiu on 2005-12-18
[QUOTE=Redindian]BTW..here's the creenshot of my desktop.[/QUOTE] Yeah, that's not a login screen problem, that's a general screen resolution problem.
[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by Redindian on 2005-12-18
I'm not a computer geek.....i did reconfigure and used the default settings in xorg file. It looks like my screen (window sizes), fonts, icons are good for 21 inch TV. I think i need to change something so that it can re-scale everything to look good for my computer screen. Give me more instructions or options to try.

---

### Post by soulestream on 2005-12-18
> I'm not a computer geek.. 

Obviously


Im sure someone would be happy to tell you how to setup you monitor. But those little hats that lets up see your monitor's model # and what video card you have are really expensive and most of us can't afford them. See most of us dont get paid to give you "immediate" help. So it would be nice if you could post what monitor and video card you have. 

If you can figure it out you might want to post your /etc/X11/xorg.conf

soule;)

---

### Post by Redindian on 2005-12-18
Here's my xorg.conf file.

Also the first 2 pages of my xorg.o.log file

"X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux indian 2.6.12-10-386 #1 Fri Nov 18 11:51:02 UTC 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Fri Nov 18 11:51:02 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 18 14:26:41 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "DELL E773c"
(**) |   |-->Device "ATI Technologies, Inc. Radeon X300 SE (RV370)"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2580 card 1028,0181 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2581 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1c:0: chip 8086,2660 card 0000,0000 rev 03 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2658 card 1028,0181 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2659 card 1028,0181 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,265a card 1028,0181 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,265b card 1028,0181 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,265c card 1028,0181 rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev d3 class 06,04,01 hdr 81
(II) PCI: 00:1e:2: chip 8086,266e card 1028,0181 rev 03 class 04,01,00 hdr 00
(II) PCI: 00:1f:0: chip 8086,2640 card 0000,0000 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,266f card 1028,0181 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2651 card 1028,0181 rev 03 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,266a card 1028,0181 rev 03 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,5b60 card 1002,0302 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,5b70 card 1002,0303 rev 00 class 03,80,00 hdr 00
(II) PCI: 03:01:0: chip 8086,1080 card 1028,1000 rev 04 class 07,03,00 hdr 00
(II) PCI: 03:08:0: chip 8086,1064 card 1028,0181 rev 03 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)"

---

### Post by Redindian on 2005-12-18
Hello,
I checked the screen resolution, i was having only 640x480 and the horizsyn and vertrefresh in my xorg.conf file weren't there. So i reconfigured xorf.conf (1024x768; horizsyn 30-70; vertrefresh 50-130) and fixed everything except (1) gnome menu fonts in the panel (2) the session fonts at login (where i choose gnome, kde or xfce) ...they all are very small.

Anyway thanks alot for all your help.

---

