---
title: "Installing Beryl on Feisty with ATI X1300"
date: 2007-05-13
forum: Desktop Effects &amp; Customization
---

### Post by LIJI on 2007-05-13
Hey,
I followed few guides in how to install Beryl on Feisty with ATI in order to get a nice-looking desktop.
Some guides told me to remove some drivers, some told me to installed XGL and some installed Beryl, but it always "Crashed" into gnome.
None of them worked, sometimes it made my X-Server refuse to run or just screw up my display.
Can someone help me installing beryl safely and step-by-step?

I'm using:
Ubuntu 7.04/Feisty Fawn, Intel Core 2 and ATI X1300.
Ubuntu is installed on an EXT2 Partition.
I have 2 hard disks divided to Ext2, Swap, NTFS and FAT32 partitions.
I also have Windows XP on a dual boot with read and write access to EXT2 partition, just in case Linux won't boot and I have to edit some files in order to get it to work.

In the image: My desktop after installing and running XGL. Image converted to 256 colors to reduce size.

Thanking in advance,
-LIJI

---

### Post by jimbo99 on 2007-05-13
Without beryl running can you run a 3d accelerated game such as Enemy-Territory, UT2003/2004, quake3 or Quake 4?

Push the settings up if it does work.  Tell us what you get--corruption or quality or crashes or slow performance, etc.

---

### Post by LIJI on 2007-05-13
Can you link me to a simple 3D game for Linux? I usually play 2D games.
Or some game that comes with the Add/Remove by default.

---

### Post by LIJI on 2007-05-15
NVM, A friend of mine guided me how to install it.

---

### Post by chrisN_uk on 2007-05-15
Could you pass on his words of wisdom? I'm in the same boat as you where...

---

### Post by manogamez on 2007-05-25
As am I!
I have gotten Compiz and Window Effects to work but Beryl is very stubborn.

---

### Post by chrisN_uk on 2007-05-26
How have you managed that? I can't even get that far. Are you using the x1300?

---

### Post by Ub1476 on 2007-05-26
To install a 3d game go to ADD/REMOVE, click on games, and then search for the 3d game. Easy as that:p Also beryl version 0.2.1 wont work with XGL.

---

### Post by richpor on 2007-06-20
> **LIJI said:**
> Hey,
I followed few guides in how to install Beryl on Feisty with ATI in order to get a nice-looking desktop.
Some guides told me to remove some drivers, some told me to installed XGL and some installed Beryl, but it always "Crashed" into gnome.
None of them worked, sometimes it made my X-Server refuse to run or just screw up my display.
Can someone help me installing beryl safely and step-by-step?

I'm using:
Ubuntu 7.04/Feisty Fawn, Intel Core 2 and ATI X1300.
Ubuntu is installed on an EXT2 Partition.
I have 2 hard disks divided to Ext2, Swap, NTFS and FAT32 partitions.
I also have Windows XP on a dual boot with read and write access to EXT2 partition, just in case Linux won't boot and I have to edit some files in order to get it to work.

In the image: My desktop after installing and running XGL. Image converted to 256 colors to reduce size.

Thanking in advance,
-LIJI

:BUMP:

I've got EXACTLY the same problem on my HP compaq nc6400 with an ATI X1300 radeon mobility.  everything seems to load fine but then I get the "shredded" screen...  I can change the resolution by remembering the keystrokes, and sometimes I can even see the destkop.

Can anyone help with this?:(

---

### Post by catfishk on 2007-07-02
this is my experience with this problem the last few months...

 i have a T60 with the ATI X1300 (R500) chipset.  the only driver i can get 3D acceleration with is the proprietary AMD/ATI fglrx driver, since open source drivers don't support the ATI R500 boards.  the proprietary drivers, however, do not support the composite extension necessary for AIGLX in feisty (in feisty XGL isn't supported, AIGLX is used)  to get around this conflict, beryl-xgl can be used if you downgrade to the edgy beryl-core package
 the disadvantage to XGL is that you can't run other 3D programs like games or rendering software along side beryl or compiz.  in AIGLX you can, and i do with my desktop and its composite compatible NVIDIA card

 i have not gotten the AMD/ATI 8.37.6 fglrx realease to work in feisty with beryl-xgl.  beryl will start but gnome locks up after the splash, everytime.  3D acceleration is extremely good in games and other software otherwise, while not using XGL.  on the same T60, with edgy, beryl-xgl worked great!

 i'd like for either the feisty restricted open source fglrx to support R500 boards (X1300, X1400, etc) or for AMD/ATI to release a driver supporting the better AIGLX used in feisty

 for a 3D game, install planetpenguin-racer in synaptic or command line apt-get

---

### Post by chrisN_uk on 2007-07-02
I'm unable to get the fglrx drivers working on my X1300. Could someone guide me through it?

---

### Post by boonwee on 2007-07-03
> **chrisN_uk said:**
> I'm unable to get the fglrx drivers working on my X1300. Could someone guide me through it?

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

this will help you get the fglrx drivers to work on x1300. if you already have ubuntu/xubuntu running except for the fglrx drivers, start from step 4 in the link above.

---

