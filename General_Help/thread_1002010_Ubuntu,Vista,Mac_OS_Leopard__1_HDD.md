---
title: "Ubuntu,Vista,Mac OS Leopard  1 HDD"
date: 2008-12-04
forum: General Help
---

### Post by kevil99 on 2008-12-04
Ive been using ubuntu for about a year. I have a friend who is interested in installing Multiple OSs on 1 HDD.

With this in mind, I dont want to give him any suggestions that may hurt or possibly damage his new PC.

His PC is built on the New Corei7, DDR3 low voltage ram and prolly tri SLI gtx 260s. so im sure there will be very little support or drivers for his system. 

Im looking for suggestions simply because hes interested in using LINUX for the first time and i dont want his experience to be a turn off. Id assume Ubuntu would be the best distro for a first time use.

Im sure that a dual boot is possible. But what first? ubuntu then vista or vice versa?

Any help would be greatly appreciated:D

---

### Post by kevil99 on 2008-12-04
? bump

---

### Post by bapoumba on 2008-12-04
Be aware that Mac OS X license allows it to be only installed on Apple hardware, and one aspect of your question will not be supported here. Thanks.

---

### Post by Skripka on 2008-12-04
Ubuntu gets installed last.  Windows in particular wants a monopoly on the bootloader.


Triple GTX260s, an LGA1366 Rig, wanting multiple OSes, and he's only wanting one harddrive??? :confused:  That is a bad place to skimp-especially when this rig is well in excess of $2k for parts.  That is a recipe for a data disaster, IMHO.  Ideally you should be able to completely lose an entire OS and the disk it is on, and not lose much---i.e. you don't lose the ability to boot the remaining OSes or lose your data.


As mentioned it is against the EULA of OSX to install OSX on non-Apple branded hardware (it is "illegal"), you want to try to pull it off-you're on your own.

---

### Post by kevil99 on 2008-12-04
Yeh his reasoning was that his HDDs connections face the back of the case so continuosly disconecting and reconnection will be a hassle.

He can afford 3 HDDs so i guess id suggest #1HDD Vista and Ubuntu. then #2 Mac.

This project need some details. any really easy to follow links would be helpful as well. Say just on dual booting. Ones ive found include using grub. Is grub easy to use? or will Vista be user friendly enough to allow Ubuntu in?

Personally Im VERY pleased using Two seperate HDDs and i just switch my sata cables

---

### Post by Skripka on 2008-12-04
> **kevil99 said:**
> Yeh his reasoning was that his HDDs connections face the back of the case so continuosly disconecting and reconnection will be a hassle.

He can afford 3 HDDs so i guess id suggest #1HDD Vista and Ubuntu. then #2 Mac.

This project need some details. any really easy to follow links would be helpful as well. Say just on dual booting. Ones ive found include using grub. Is grub easy to use? or will Vista be user friendly enough to allow Ubuntu in?

Personally Im VERY pleased using Two seperate HDDs and i just switch my sata cables

Windows will not recognize any other OS on any other drive--regardless of what file system it uses.  

GRUB is easy, not aesthetically pretty-but easy-BUT Ubuntu and GRUB MUST be installed AFTER Windows..


[U][I]**The Skripka, nearly foolproof (knock on wood) method of sandboxing/safegaurding and booting multiple OSes:**
[/I][/U]
Ubuntu and Windows are BEST kept on seperate drives, with the Ubuntu drive being the primary drive in BIOS boot order, and with GRUB installed to the Ubuntu drive.  

Why this way?  Because if GRUB dies for whatever reason, you can make your Windows drive the primary drive in BIOS-and still boot it.  Or, If Windows dies and takes the MBR with it-you can still boot Ubuntu-also...................if the user chooses to instead modify the Windows MBR and add GRUB to it-and then GRUB dies (for whatever reason), you're left with not 1 but two dead unbootable OSes.  That then need fixing. 

Of course-the Ubuntu drive should be in 3 seperate partitions to begin with (root, home, and swap--ALL seperate).



Call me paranoid-but I speak from experience.  If you sandbox-like the above, odds are regardless of what disaster happens-it is very unlikely that you will lose much more than a few hours of time and effort.  If you put all your eggs in one basket, you can lose a great deal in a hurry-and you waste even more time trying to get things back to where they were.


PS-what kind of wacky board has SATA headers facing the back of the board???? :confused:

---

### Post by kevil99 on 2008-12-04
lol the connections on the _HDDs_ are facing the back of the case.

i belive in this case i should tell em to do as ive done.

1 OS per HDD
and face the connectors out in the bays;)

---

### Post by Berettamato on 2008-12-04
Hi all,

 I am Kevil99's friend. Here is my setup and problems. The motherboard is a EVGA X58 TRI SLI [http://www.evga.com/PRODUCTS/enlarge.asp?PN=132-BL-E758-A1&I=5](http://www.evga.com/PRODUCTS/enlarge.asp?PN=132-BL-E758-A1&I=5) . There is ten SATA on the MOBO eight are hidden by the three GTX260's so I would have to remove them every time to change the cables. There one not blocked but it is for E-SATA and I am using it for the case E-SATA. The last is a E-SATA on the back I/O and is used for my 2gb back drive. As for the case it is a Lain-Li pc-x2000b [http://www.lian-li.com.tw/v2/en/product/product06.php?pr_index=258&cl_index=1&sc_index=25&ss_index=61&g=q](http://www.lian-li.com.tw/v2/en/product/product06.php?pr_index=258&cl_index=1&sc_index=25&ss_index=61&g=q) . It has a six bay hot swap for the HHD's. This mean I would have to pull the HHD's that be a pain and I don't want to go into the case that much. Thank you all for your help.

Here is my parts lists.

CPU
Intel Core i7 920 2.66GHz 4 x 256KB L2 Cache 8MB L3 Cache LGA 1366 Quad-Core

RAM
CORSAIR DOMINATOR 12GB (6 x 2GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Triple Channel Kit

MOBO
EVGA 132-BL-E758-A1 LGA 1366 Intel X58

GPU
(1)XFX GX260NADDU Geforce GTX 260 XXX Edition 896MB GDDR3 448-bit GDDR3 PCI Express 2.0 x16  SLI
(2)XFX GX260NADDU Geforce GTX 260 XXX Edition 896MB GDDR3 448-bit GDDR3 PCI Express 2.0 x16  SLI
(3)XFX GX260NADDU Geforce GTX 260 XXX Edition 896MB GDDR3 448-bit GDDR3 PCI Express 2.0 x16  SLI

HHD
Raid-0
(1)Western Digital Raptor WD1500ADFD 150GB 10000 RPM SATA 3.0Gb/s
(2)Western Digital Raptor WD1500ADFD 150GB 10000 RPM SATA 3.0Gb/s
NON-RAID
(3)Western Digital Caviar Black WD1001FALS 1TB 7200 RPM 32MB Cache SATA 3.0Gb/s
(4)Western Digital Caviar Black WD1001FALS 1TB 7200 RPM 32MB Cache SATA 3.0Gb/s
(5)Western Digital Caviar Black WD1001FALS 1TB 7200 RPM 32MB Cache SATA 3.0Gb/s
(6)Western Digital Caviar Black WD1001FALS 1TB 7200 RPM 32MB Cache SATA 3.0Gb/s

DVD
(1)Sony NEC Optiarc Black  2MB Cache SATA 20X DVD±R Burner
(2)Sony Black 2X Blu-ray DVD-ROM 8X DVD-ROM 24X CD-ROM SATA Internal 2X Blu-ray DVD ROM

PSU
SILVERSTONE ZM1200M 1200W ATX 12V 2.3 & EPS 12V SLI Ready CrossFire Ready Modular Active PFC

CASE
LIAN LI PC-X2000B ATX

CPU COOLER
Thermalright Ultra-120 eXtreme-1366 RT

KEY/MOUSE
Logitech G15 2-Tone 104 Normal Keys 29 Function Keys USB Wired
Logitech G9 Black 5 Buttons Tilt Wheel USB Wired Laser 3200 dpi Gaming Mouse

MONINTOR
(1)Hanns·G HG-281DPB Black 28" 3ms Widescreen LCD HDMI Monitor 500 cd/m2 800:1
(2)Hanns·G HG-281DPB Black 28" 3ms Widescreen LCD HDMI Monitor 500 cd/m2 800:1
(3)Hanns·G HG-281DPB Black 28" 3ms Widescreen LCD HDMI Monitor 500 cd/m2 800:1

SOUND
(1)Denon AVR-589 5.1 CH Home Theater Receiver  
(2)Polk Audio RM10 5-Pack 5CH Home Audio Speaker System
(3)Polk Audio PSW111 Black Single Compact powered subwoofer

MSC
Matrox TripleHead2Go Digital Edition T2G-D3D-IF DVI Interface (5760x1200 resolution)
D-Link DGL-4500 IEEE 802.3/3u, IEEE 802.11a/b/g, IEEE802.11n Draft Xtreme N Gaming Router
Macbook Pro 15.5"

---

### Post by TeXtonyx on 2008-12-04
Skripka wrote: "Windows will not recognize any other OS on any other
drive--regardless of what file system it uses."

Some people might think there are more implications to that statement
than meets the eye. For instance, Windows will do dual or multi-boot
other OS on two drives. Easybcd will boot across two drives and XP
uses free Bootpart along with installing *nix grub to the /boot partition.
LinuxReader, a free program for Windows, will let you see your *nix
partitions across two drives and copy save files from them to the
Windows partition. It is true that Computer Management just shows
you occupied other spaces labeled usually healthy and unknown.

Two drives is a great idea. I think you should install Vista to
the first drive because that keeps its MBR safe from overwrites.
Using the Ubuntu live cd at Step 7, Advanced, one can change grub
from the MBR to Ubuntu's /boot partition. Then it can be booted
by Vista. I think some other *nix OS could be installed in the
second (not counting swap) partition of the second drive and let
it occupy the MBR. With this quality setup the bios most likely
will offer a keyboard F-key to boot either drive. I make every OS 
capable of booting every other OS, though Vista would indirectly
boot Ubuntu, and Ubuntu's menu.lst would include the other *nix.
Maybe you should have Gentoo on a partition since you will need
lots of practice compiling drivers one would imagine. 

One day I'm going to have a nice system too after driver support
and programs for x64 is common, and motherboards don't charge
an arm and a leg to recognize and employ 32GB or ram, 9 is nice! 
What video card did you/OP choose to support 3 monitors and I
suppose 3d gaming? Can you design special effects for movies?

---

### Post by Berettamato on 2008-12-04
Thank you for your input I must be honest most of what you said flew over my head at speeds that knocked me out of my orthopedic gaming chair. Luckily I broke the fall for my beer.

I am a gaming system builder and want to raise my software knowledge past the n00b statutes. So I made a deal with the Devil and bought a mac on order can't wait. Signed up at the local CC for A+ classes. I know hardware like Bruce lee know how to break bones.The problem is I am Steve Urkel on spring break in Mexico judging a wet T contest when software is involved. Kevil & my buddy Stalker talk about Linux 24/7. So hear I am.

I just ordered a second set of 6gb instead of the extra 3gb. New total 12GB.

---

### Post by kevil99 on 2008-12-04
Despite you knowledge level of linux Im possitive youll take to linux pretty quick bro. Start out with a popular distro such as Ubuntu. if ya dont find it to be easy try Kubuntu. It has a different desktop environment. Warrior ran it about a year ago and preferred it over Ubu. Any questions you have are very very simply resolved with google or great forums such as this one!

Altho this is an Ubu.forum there are many different distros to choose from. [http://distrowatch.com/](http://distrowatch.com/)  is a really great place to see the latest flavors. Be forewarned it gets really addictive if your into trouble shooting. Personally im on a role with adding games to my box.  Yes COD4 has been succesfully ran!
CZ is a breeze.

Wine is a great app to aid in gaming. [http://appdb.winehq.org/](http://appdb.winehq.org/)
and there are many many other cool things ya can do also. bet ya never seen windows do half the things Compiz does.

I need another |DF| brother to chat with about this stuff from time to time since stalker stays in the shadows.

---

### Post by starfry on 2009-02-18
Wow that is one hell of a spec!
I too am poised to take the plunge into core i7. I would be very interested in your experiences with 64 bit Ubuntu on the core i7 platform. Hopefully you can post an update when you get it working...

ps. Steve Urkel Rocks! *Did I do thaaat????* :D

---

