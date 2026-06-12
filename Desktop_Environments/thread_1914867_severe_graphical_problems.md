---
title: "severe graphical problems"
date: 2012-01-25
forum: Desktop Environments
---

### Post by TheRacerX on 2012-01-25
i recently reverted back to Ubuntu 10.10 because Ubuntu 11.10 put too much strain on my older desktop computer, ive never had issues with Maverick until my most recent reboot now everytime i boot into the standard desktop environment its got HUGE graphical glitches, menus wont show, my screentlets flicker and disappear, i cant do anything, if anyone knows what might be wrong let me know, ive never had these kinds of problems with Maverick on this computer before now. 

Note: everything works fine if i boot in Ubuntu Desktop Environment(safe mode)

---

### Post by typhoon_tip on 2012-01-25
Let me guess, you have an ATI card and FGLRX driver installed, and you are using Gnome 3 ?

---

### Post by TheRacerX on 2012-01-25
nope Maverick Meerkat using the onboard Intel chipset of my Pentium 4 powered Dell Dimension 3000

yes i know im running a dinosaur for a computer

---

### Post by typhoon_tip on 2012-01-25
> **TheRacerX said:**
> nope Maverick Meerkat using the onboard Intel chipset of my Pentium 4 powered Dell Dimension 3000

yes i know im running a dinosaur for a computer

Loll it doesn't matter how old. Can you do a:
```
lspci
```

... and post the result here ?

Tks

---

### Post by TheRacerX on 2012-01-25
theracerx@MaximumRide:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]
01:02.0 Multimedia audio controller: Yamaha Corporation YMF-754 [DS-1E Audio Controller]
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

heres the results you asked for

---

### Post by typhoon_tip on 2012-01-26
You are running a dual graphic card config, the laptop is not that old after all.

Try to see if you can disable the onboard graphic card in the BIOS (set the computer to run with Discrete/ATI card only).

By the way, you can give a shot to Ubuntu 11.10 now: ATI/AMD just released 12.1 Catalyst today and Gnome 3 is working !!

---

### Post by TheRacerX on 2012-01-26
its not a laptop its a desktop computer i have the ATI card disabled in the bios already cause its not fast enough to play videos but the onboard chipset is for some reason, so i highly doubt its the result of a conflict also my ATI card doesnt use the proprietary driver it uses the open source one from the Synaptic Package Manager.

sorry i mean the X.org driver

---

### Post by typhoon_tip on 2012-01-26
> **TheRacerX said:**
> its not a laptop its a desktop computer i have the ATI card disabled in the bios already cause its not fast enough to play videos but the onboard chipset is for some reason, so i highly doubt its the result of a conflict also my ATI card doesnt use the proprietary driver it uses the open source one from the Synaptic Package Manager.

sorry i mean the X.org driver

It's not fast enough because you probably weren't using FGLRX. Try the reverse: disable intel, enable ATI, then try to install the FGLRX driver (it should propose you to do so). I am not sure if that intel card is the one causing problem sometimes, there are some that does.

EDIT: sorry, your card is not supported on Linux... Only on Windows (there is no available AMD driver). You could try a cheap ATI/NVIDIA that is supported (check first).

EDIT2: give Ubuntu 11.10 a shot. The Open Source ATI driver support 2D and 3D acceleration. Before install, disable INTEL in Bios and enable ATI.

---

### Post by TheRacerX on 2012-01-26
i had 11.10 on here before this computer only has 1GB of RAM and a 2.8GHz Pentium 4 it lagged the computer down something awful so i got rid of it i tried Xubuntu and it was horrible cause i couldnt get the sound to work so i went back to the version of Ubuntu ive ALWAYS used and i know worked and thats Maverick Meerkat and now even its not working properly

---

### Post by typhoon_tip on 2012-01-26
But did you do a clean re-install of Maverick ?

Anyway, my suggestion is this: install Ubuntu 11.10 (clean install), and get into Unity once. Do all updates. After that, run this command:
sudo apt-get install xfce4

After is done, logoff and login to Xfce (choose it from the gear icon). 1G of RAM is more than sufficient for the scope ! :popcorn:

---

### Post by robergeb on 2012-01-26
I had a similar problem with my ATI graphic card on Ubuntu 11.10. This code fixed the issues.

Open the terminal while booting and type the following code lines:

sudo /usr/share/ati/fglrx-uninstall.sh # (if it exists)
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

Hope this is useful.

---

### Post by TheRacerX on 2012-01-26
yes i did a clean install, and everything was working fine....until after i updated the X.org intel driver....i think i may have figured out the problem lol and no i wasnt a fan of the XFCE environment...im just going to suffer through running my Windows XP partition until i get my new All In One PC in March i think

also of note my ATI card isnt having graphical issues its just an older card that doesnt have a fast enough GPU to run videos cleanly it only has a 150MHz GPU and 64MB of Video RAM

---

