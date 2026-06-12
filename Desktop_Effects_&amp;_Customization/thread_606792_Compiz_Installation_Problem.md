---
title: "Compiz: Installation Problem"
date: 2007-11-08
forum: Desktop Effects &amp; Customization
---

### Post by warmwaddle on 2007-11-08
Hi all,

I am an extreme noob at Linux. Switching from Windows, I am so used to all programs installing themselves. I have downloaded compiz and now I'm stuck on installation. I read a file in the pack, it said this. compiz uses libstartup-notification which is available at
[ftp://ftp.gnome.org/pub/GNOME/sources/startup-notification/](ftp://ftp.gnome.org/pub/GNOME/sources/startup-notification/)

compiz uses automake, in order to generate the Makefiles for compiz use:

	$ autogen.sh

After that, standard build procedures apply:

	$ make
	# make install
I went to the link and downloaded that thing... but how the heck do I install that also?! :confused: As for those codes they mentioned, they are meaningless to me. Where do I put them? So, can anyone give me a step by step tutorial?

EDIT: Compiz fusion is what I want! I got the tarball and ran those command exe things.... doesn't seem to do anything.

---

### Post by mrmiserable on 2007-11-08
as a noob i suggest you install packages from main menu/system/administration/synaptic package manager not download and compile as this can be awkward

secondly compiz can be hard to work as it is dependant on your graphics card

lspci in terminal will tell you your graphics card

synaptic is just as easy as windooooows

---

### Post by warmwaddle on 2007-11-08
Ok in that application I found compiz fusion. How do I install? That program is confusing.

---

### Post by Can+~ on 2007-11-08
[LIST=1]
[*]If you're in Ubuntu 7.10 (Gutsy Gibbon) you already have compiz-fusion installed on your system.
[*]If you're on Ubuntu 7.04 (Feisty Fawn) or lower; compiz fusion is already in synaptic, therefor, you don't need to make, nor compile anything. Go to System > Administration > Synaptic package manager.
[*]In windows you have "Add/Remove programs", but that's a lie, it only "Removes/Fixes" programs. In ubuntu, in Applications > Add / Remove you can **really add programs from the rep server**.
[*]Finally, is you ever need to compile source codes, it usually works like this: Read the "README" or manual about that particular application.[LIST]
[*]The most typical thing is that they ask you to do something like "./configure" on terminal.
[*]Then make
[*]Then make install
[/LIST]
[*]Also, compiz-fusion demands accelerated graphics support. Nvidia drivers are a cakewalk to install, but ATI's fglrx is a pain on the butt.
[/LIST]

---

### Post by warmwaddle on 2007-11-08
Hmmm... I have Gutsy. So it's already here? All I see is beryl. System > preferences doesn't have it! How do I set it/enable it? Oh, and Compiz-Fusion isn't in the program manager thing.

---

### Post by Can+~ on 2007-11-08
System > Preferences > Appearence > Tab: "Visual Effects".

If you want the "Customized settings" you can either do:
> sudo apt-get install ccsm

Or look for it in add/remove.

This is how it should look like after installing ccsm: (If not, then the last option is invisible)
[http://img.photobucket.com/albums/v517/CanXp/visualFX.png](http://img.photobucket.com/albums/v517/CanXp/visualFX.png)

---

### Post by warmwaddle on 2007-11-08
There is no appearence in my preferences. Not in add remove programs. I did the command and the terminal said this.
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ccsm



---

### Post by Can+~ on 2007-11-08
Sorry, the actual name is 
> compizconfig-settings-manager

No Appearence in system? Are you sure you're using Gutsy?
"About Ubuntu" in system should say what version you're using.

---

### Post by Forlong on 2007-11-08
Yeah, sounds like you're not on Gutsy at all. Beryl is another indicator, that should have got removed in the upgrade process.

What's the output of
```
lsb_release -a
```

---

### Post by warmwaddle on 2007-11-08
Holy cow! I am still feisty! (rawr) How do I update my system? And also how do I set up compiz-fusion? Oh, and finaly, when I update my system will it interrupt my downloads in progress? I have 3 currently. (kubuntu, edubuntu, and xubuntu.) Soo... yea...

---

### Post by Forlong on 2007-11-08
> **warmwaddle said:**
> Holy cow! I am still feisty! (rawr) How do I update my system?
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)
> **warmwaddle said:**
> And also how do I set up compiz-fusion?
[How to set up Compiz Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)
> **warmwaddle said:**
> Oh, and finaly, when I update my system will it interrupt my downloads in progress?
No, but I wouldn't recommend doing both.

---

### Post by haunticious on 2007-11-08
basically don't worry about upgrading to gutsy just yet there's not much need at the moment. You need to tell us what graphics card you have and if you don't know open a terminal applications>accessories>terminal and type lspci. tell us what it says once you've typed that and we can move on to installing compiz-fusion.

---

### Post by warmwaddle on 2007-11-08
Thanks guys, i'll update ya after I get gutsy and finish my downloads. (6 hours)

For my graphics card, find it in the mess the terminal gave me:
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
05:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
05:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
05:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
05:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
05:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

---

