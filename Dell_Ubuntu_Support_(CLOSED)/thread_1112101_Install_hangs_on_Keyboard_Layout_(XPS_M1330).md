---
title: "Install hangs on Keyboard Layout (XPS M1330)"
date: 2009-03-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by collitis on 2009-03-31
Hello:

Have had success installing Ubuntu and Kubuntu on laptops in the past, but have run into a snag.

Trying to install Kubuntu (I'll settle for Ubuntu) onto a Dell XPS M1330. The install stops after I select the Keyboard Layout (Step 3) and the partitioner gets loaded. It just sits there on the Keyboard Layout screen, doing nothing, and yet, in both Live-CD install and install straight from the boot menu, I can cancel out of the install, so the system's not frozen. I have tried both 8.10 and 8.04, Ubuntu and Kubuntu, CD and USB Thumbstick, straight off the boot menu and through the Live CD interface, in every combination possible. It all does the same thing-it hangs on screen 3 until I cancel out of it.

My Specs:
Dell XPS M1330
  BIOS: A12 (07/08/08)
  RAM: 2GB (2x 1024 PC2-5300)
  WLAN: Dell Wireless 1490 Dual Band WLAN Mini-Card
  Ethernet: Broadcom Netlink (TM) Fast Ethernet
  CPU: Intel Core2 DUO T7500 @ 2.20GHz
  Optical Drive: Matshita DVD+-RW UJ-857G ATA Device
  Audio: SigmaTel High Definition Audio
  Graphic: NVIDIA GeForce 8400M GS
  HDD: Western Digital Scorpio 160GB (WD1600BEVT)

Have searched the forums and Googled the problem and I haven't had much luck finding a cause except low RAM, which isn't the case here.

Your assistance is appreciated.

---

### Post by collitis on 2009-04-04
Forget it. I fixed it.

---

### Post by cupoange on 2009-05-25
what did you do to get it to work?  I am having the same problem.  I had 8.10 intrepid installed dual boot with XP, and I wanted to wipe both and install 9.04 fresh.  the installer hangs after selecting the keyboard layout.

thanks.

---

### Post by oatkinson on 2009-06-05
I am having the same problem on a lenovo T500. How did you fix it?

---

### Post by bigkah624 on 2009-07-18
I am/was having a similar problem. It sort of fixed itself -- what seems to be happening is that it is scanning all the attached drives and can hang if there are some errors on the drive or if the drives are old or large or... 

Mine eventually "unhung" itself after I waited long enough (like 10 mins?) and only showed one of my drives. I'm guessing the other drive is the bad drive which is what was causing the hanging. Anyway, that's my guess inspired by the thread here: [http://ubuntuforums.org/showthread.php?t=531871](http://ubuntuforums.org/showthread.php?t=531871) and by my own experience.

I'm actually installing 9.04 right now...

---

### Post by dannymichel on 2010-04-18
> **bigkah624 said:**
> I am/was having a similar problem. It sort of fixed itself -- what seems to be happening is that it is scanning all the attached drives and can hang if there are some errors on the drive or if the drives are old or large or... 

Mine eventually "unhung" itself after I waited long enough (like 10 mins?) and only showed one of my drives. I'm guessing the other drive is the bad drive which is what was causing the hanging. Anyway, that's my guess inspired by the thread here: [http://ubuntuforums.org/showthread.php?t=531871](http://ubuntuforums.org/showthread.php?t=531871) and by my own experience.

I'm actually installing 9.04 right now...
i know for a fact that all my drives and hardware are fine, but mine is still hanging. i'm giving it another 10 minutes until i give up

---

### Post by mpanichi on 2010-06-17
I'm having the same problem. Any tip on how to solve it?

The PC is brand new (the HDD is "virgen") and I'm booting it from a USB disk.

It hanged after step 3 both when I used the installer on desketop as well as when I reboot and chose the Install option on the boot menu...

The HDD is 500gb and MoBo is Atom.

Tks

---

### Post by pishta on 2010-06-18
try the "alternate CD install" available from your favorite Ubuntu download page. Its more command line looking, not as GUI, but not in black and white either. It worked for me, getting past my mysterious hang.

---

### Post by mpanichi on 2010-06-18
Tks for the tip! However it didn´t work because it need a CD-ROM installed on the computer...I could boot and advance many steps on the installation however it started to look for drivers and packages in CD-ROM, meanwhile it should look as USB...so I couldn´t go further. ATB

---

### Post by NilsOscar on 2011-09-25
I solved this by very quickly accept the default keyboard choice and move on to the next installation step. 
 
Now I will have to change keyboard layout later, when the istallation is finished. Hope Ubuntu remembers it. It does not do so in my virtual vmware installation. 
 
(My pc is a Sony Vaio Laptop whith dual core Intel processor.)

---

### Post by bobsageek on 2011-09-25
I ran into this on the my attempted install on my Dell N7010 (17r bought this month), fixed it by removing my Logitech USB transceiver during the install, seems to have been hanging up detecting input devices (since the Logitech mouse buttons emulate keyboard strokes in some cases). 

Did not run into this issue on 11.10 Beta 2.

---

