---
title: "Problems with inspiron 1420 &amp; gusty (bluetooth + brightness ctrl keys)"
date: 2008-03-05
forum: Dell  Ubuntu Support
---

### Post by delca5 on 2008-03-05
Hi people, i have my new shiny dell inspiron 1420 (t5450, 2gb ram, 120 hd, bluetooth, wifi intel 3945ABG, webcam, 8400 gs).
I installed the ubuntu remastered 7.04, and almoast everything works, except bluetooth and webcam. Because of that i downloaded the dvd of gusty from dell for 1420, with the hope that this new version solved my problems but it didnt.
Now the bluetooth, webcam, and the  brightness ctrl keys dont work.
here is my lspci
0:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

and my lsusb
Bus 006 Device 001: ID 0000:0000
Bus 007 Device 002: ID 05a9:2640 OmniVision Technologies, Inc.
Bus 007 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 002: ID 045e:0009 Microsoft Corp. IntelliMouse
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0a5c:4503 Broadcom Corp.
Bus 001 Device 003: ID 0a5c:4502 Broadcom Corp.
Bus 001 Device 002: ID 0a5c:4500 Broadcom Corp.
Bus 001 Device 001: ID 0000:0000

Except for this thinks im very pleased with ubuntu, i have now 1 hour plus of battery than vista premium!
thanks to all & greetings from Argentina.
PS:Sorry for my english

Solution found!
Horrible but ... Install XP/Vista, the bluetooth light will turn it on (you must download a fix from dell page if xp is installed), then reboot to ubuntu and then magic!, the bluetooth device will magicly work!
--------Dell this solution sucks!, please release a bios or something that enabled the bluetooth device since boot and then you can sell inspiron 1[4,5,7]20 with everything working!.-------
Bye
PS: until now in ubuntu feisty 2.6.22-14-generic everything works (except brightness keys blame 2.6.22 kernel from gusty)
in ubuntu feisty with 2.6.20-generic kernel works all except webcam (the new kernel fix this)
Now im using 2.6.22 kernel, i have webcam, and this new kernel have NO_HZ ([http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)).

---

### Post by notwen on 2008-03-05
I cant speak for the webcam, as I have the original Inpsiron 1420n which did not offer a webcam option upon customizing.  After installing the custom Dell Gutsy image onto my Inspiron 1420n, my brightness Fn keys and bluetooth both work out-of-the-box.  I only have a mouse and my cell phone to test my bluetooth, what devices are you trying to connect?

---

### Post by delca5 on 2008-03-05
Yes its strange in feisty these keys work flawless, but now ... at least the multimedia works ok.
the bluetooth device itself dont work
My inspiron only say "inspiron 1420", there is not "n", but in the webpage for customization the bluetooth is the "INT 355 BLUETOOTH WRLESS"
[http://lastore.dell.com/store/frameset.asp?c=ar&cs=ardhs1&entity_key=INSP1420_AR&entity_type=CFGSET&l=es&s=dhs&shopper_country=ar&shopper_language=es&shopper_segment=dhs&store_key=LATRANS](http://lastore.dell.com/store/frameset.asp?c=ar&cs=ardhs1&entity_key=INSP1420_AR&entity_type=CFGSET&l=es&s=dhs&shopper_country=ar&shopper_language=es&shopper_segment=dhs&store_key=LATRANS) 

gonza@dell-1420:~$ hcitool dev
Devices:
gonza@dell-1420:~$

i already try restarting the service ( /etc/init.d/bluetooth restart )
What module of the kernel is responsable for doing the bluetooth work ?
And the keys i think there must be a app that ctrl this, maybe this app is missing... I dont know.
Thank for the replay.
Bye.

---

### Post by notwen on 2008-03-05
[Here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Camera_Does_Not_Work") is the fix for your webcam.  I'll look more into your bluetooth issue when I get home and have my laptop available to me.

Be sure to constantly check [Dell's Linux Wiki]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10") for updates/fixes for the Dell-buntu models.  =]

---

### Post by delca5 on 2008-03-05
Ok thanks for the webcam fix!, but im back to feisty, and have only the bluetooth problem...
Thanks.
bye

---

### Post by delca5 on 2008-03-07
I now on feisty, and i found something interesting...
I upgraded my feisty 2.6.20 kernel to 2.6.22 (i have the 2 images), because NO_HZ (google powertop for more info).
I think the problem with the keys, its maybe in the kernel 2.6.22, with this kernel and my actual feisty installation, this "special" keys dont work.
I still have the no bluetooth problem with both kernels, and the webcam work ok with the gusty kernel, with the 2.6.20 not .
Maybe this can be usefull for someone, bye.

---

