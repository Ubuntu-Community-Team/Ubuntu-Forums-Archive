---
title: "Installing ATI Proprietary Drivers after a new install."
date: 2006-05-28
forum: Desktop Environments
---

### Post by jvandecar on 2006-05-28
[size=1]**Current Rig is DualBoot:  **[color=tomato][b]Windows XP Pro SP2[color=gray]<>[/color]ubuntu 5.10
 
DFI LANPARTY UT nF4 Ultra-D - 07/02 BIOS[color=gray]<>[/color]AMD 3800+ X2 @ 2.50ghz- XP120 w/Panaflo
1gig Corsair DDR 466 @ 500mhz 3-4-4-8[color=gray]<>[/color]ASUS ATI - EAX850 XT[color=gray]<>[/color]Audigy MP3+
Twin Seagate 7200.7 200gig HDD in RAID 0[color=gray]<>[/color]WD740 Raptor[color=gray]<>[/color]Plextor PX-708A[color=gray]<>[/color]Plextor PX-116A[color=gray]<>[/color]NEC 3540 Dual Layer Burner
Lian Li PC82 Windowed Case[color=gray]<>[/color] Enermax EG701AX-VE 600w Powersupply[color=gray]<>[/color]Sony Trinitron E540 21" CRT
Adelphia Powerlink 4000/512[color=gray]<>[/color]Klipsch Promedia 5.1[color=gray]<>[/color]APC SmartUPS 1500[/size][/color][/b]

The above is my system setup.

The 74gig Raptor is connected via SATA to SATA 3 on the motherboard and is the PRIMARY with the two 200gig Seagates in RAID 0 on SATA 1 and 2.  For ubuntu purposes, the Seagates are not there.

The 74gig Raptor is partitioned into 10gig, 2gig and 62ish gig partitions.
The 10gig is my ubuntu partition and the 2gig the swap partition.

Installation came from the 5.10 iso installation CD.

After installation, the xserver would not start.

I logged into the terminal, ran ```
$ sudo dpkg-reconfigure xserver.xorg
```

There I was given many things to choose from, I tried ATI first, went through the rest, and rebooted.  No go.

I tried ATI with INT10 disabled, saw that I should do that somewhere.  No go.

I finally went back to selecting VESA and am writing this on a 60hz refresh rate which is killing my eyes.

Now, there are several different ways that I have found through searching that I should be able to install the ATI drivers.

1-  [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
2-  [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.25.18-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.25.18-inst.html)

3-  [http://help.ubuntu.com/starterguide/C/ch04.html#installatidriver](http://help.ubuntu.com/starterguide/C/ch04.html#installatidriver)
4-  [http://doc.gwos.org/index.php/Install_latest_ATi_Drivers_%288.24.8%29](http://doc.gwos.org/index.php/Install_latest_ATi_Drivers_%288.24.8%29)

First off, anything with --aticonfig doesn't seem to work with ubuntu.  So that knocks the first and second.

I'll be back with another chapter soon.

---

### Post by jvandecar on 2006-05-28
3 Doesn't work.

---

### Post by jvandecar on 2006-05-28
Well.

4 Did something different.  I now have ATI Control to click on, however it says "Driver does not provide FireGL X11 Extensions, panel components will operate only partially".

WTF is that?  I do not have a Fire card, nor have I ever selected anything saying I did.  I'm really bumfuzzled here and about ready to take smoking back up.

---

### Post by mattlaughs on 2006-07-11
Did you ever come up with any sort of solution for this? I'm still stuck with the error when trying to rpm the binary drivers from ati's site.

During the rpm -i I did get the following error:

ln: creating symbolic link `/usr/lib/fglrx/libGL.so' to
`/usr/lib/fglrx/libGL.so.1.2': No such file or directory
ln: creating symbolic link `/usr/lib/fglrx/libGL.so.1' to
`/usr/lib/fglrx/libGL.so.1.2': No such file or directory

I pointed the symlinks to the correct location /usr/X11R6/lib/...

but no avail, still get the same error message. If you have come up with a solution since posting here please let me know, as you I am very pissed off at ATI for their linux driver support BS ;)

---

