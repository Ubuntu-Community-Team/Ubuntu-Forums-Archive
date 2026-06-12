---
title: "nVidia GT 525M (Dell Inspiron 15R-N5110) still not working after 12.10"
date: 2012-10-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by leejkdnux on 2012-10-23
I created this thread to draw some attention to this problem:
[http://ubuntuforums.org/showthread.php?t=2055818&page=2](http://ubuntuforums.org/showthread.php?t=2055818&page=2)

Dell shipped lots of these cards in Inspiron N5110 series. Serious problem is: they don't work with linux!

something is wrong with detection of hardware, and nVidia GT 525M cards are always falsely and wrongly detected as nVidia GT 540M!

that creates problem with driver installation - it is impossible to install and use nVidia drivers which otherwise should work without problems.

this is serious and huge problem for all Dell linux users with that specific graphics card.

the problem is same in Ubuntu 12.04 and 12.10 and all variants, Mint, Fedora, openSUSE, and all other distros both custom and official (all x64)... Mint 13 at least detects intel Sandy Bridge graphics and applies driver for that. ubuntu just marks driver as 'unknown', and no proprietary drivers are ever detected. anyway, i don't care for intel much, i want my nVidia to work! while booting ubuntu livecd session, 3D graphics work, but driver is 'unknown'. after HDD installation, 3D acceleration no longer works, and it is impossible to run any 3D app. 2D works with X.org

i don't know what to do and whom to report, but it is really frustrating. i want to use linux as my main and only OS, but without working graphics card it is impossible...

i'm hoping for some patch or fix or something that will enable linux sys to properly detect hardware nVidia GT 525M card, and then i think there will be no problems with nVidia driver installation...

---

### Post by oldfred on 2012-10-23
I do not know if your optimus setup has the same nVidia issue as the rest of us with full nVidia cards.

They left out the headers, so it cannot recompile with the nVidia driver correctly.

Has most bug reports:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341)

[https://bugs.launchpad.net/fglrx/+bug/1068456](https://bugs.launchpad.net/fglrx/+bug/1068456)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1068488)
[https://bugs.launchpad.net/fglrx/+bug/1068661](https://bugs.launchpad.net/fglrx/+bug/1068661)

Has what worked for me, install headers & dpkg update.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068942](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068942)

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that: 
sudp apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo dpkg-reconfigure nvidia-current

Above worked for me yesterday. But today I rebooted and had same issue. I installed the nvidia-current-updates version, re-ran the dpkg reconfigure (it saw headers were still there),  and rebooted and then it worked again.

---

### Post by leejkdnux on 2012-10-24
thank you for your kind reply, my good sir.

though i must admit that i didn't have the slightest idea of what i was doing - i just mirrored your steps above nonetheless...

unfortunately lspci still shows this:

01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 04ca
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at f6000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nvidia_experimental_304, nouveau, nvidiafb

still claims to be 540M (how rude!) and still fails to work properly. actually it fails to work at all... for instance - compiz immediately crashes after login (so i must switch to kwin window manager). Blender - being 3D app as it is - crashes instantly and i can't even run it...

in case you're wondering what the hell am i talking about - i'm currently not exactly using core original ubuntu, but rather custom enhanced distro with lots of pre-installed software, which is based on ubuntu 12.04 - the [Ultimate Edition 3.5]("http://ultimateedition.info/")

but it's perfectly the same thing - same problem is present on all distros - but only good people of ubuntu community stand the chance of ending this graphical malice.

as i explained already, i tested pretty-much all major linux distros, especially ubuntu and it's variants - and i can say that nVidia evil lurks everywhere! i perfectly understand the feelings of our friend [Torvalds]("http://www.youtube.com/watch?v=iYWzMvlj2RQ") in his noble quest...

but today - first time in history of nVidia GT 525M oppression - 'additional drivers' feature actually managed to detect ONE proprietary driver for download and activation: Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library - whatever that means...

i'm going to try it just now. "WARNING: This is an unstable beta driver." first of all why should one write 'an unstable' when 'unstable' already consists 'an'? secondly, nvidia seems to be very unstable company anyway, as our friend [Linus]("http://www.youtube.com/watch?v=iYWzMvlj2RQ") loves to point out... so i predict that my unfortunate Dell Inspiron shall probably blow after installation, or something like that. if you don't hear from me again - i probably exploded with it, but know that your effort was appreciated...

Regards from the one who took it with him

---

### Post by leejkdnux on 2012-10-24
installation failed!

well i'd be happier if i had exploded!

i'll attach a log file - no sense in copying dozen pages of code...

---

### Post by oldfred on 2012-10-24
I do not know about optimus dual video systems. I think Linus was complaining about the lack of support from nVidia on optimus systems.

nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Switchable Graphics is killing my Ubuntu Experience - see post #9
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)


Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

---

### Post by leejkdnux on 2012-10-24
well, after following your previous instructions, i did this steps from here: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

You need to open your [terminal]("http://askubuntu.com/questions/38162/what-is-the-terminal") and enter the commands below. 

[LIST=1]
[*]sudo add-apt-repository ppa:bumblebee/stable 
[*]For more up-to-date nvidia drivers, you need to add another PPA. As  of 12.04, this is still necessary for Nvidia GT 6xxM cards. It may be  optional for the GT 4xxM and GT 5xxM series on 12.04. When in doubt,  just install it. The command is: sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
[*]sudo apt-get update 
[*]Install Bumblebee using the proprietary nvidia driver: sudo apt-get install bumblebee bumblebee-nvidia 
[*]Reboot or re-login
[/LIST]

and it seems to be working! i also ran apt-get update and upgrade just to feel refreshed...

intel driver is active and i can use 3D. compiz works. i tried running Blender with 'optirun' and it also works. currently i have no way of testing is it really nVidia or how well does it perform, but i intend to find out that soon. i'll install some games with wine and try to run them with optirun and check performance...

thank you for your support and valuable info.

this is still not final solution but it is very precious current workaround for me. i love linux and hope that in the future it will become standard platform, widely used and with first class driver support! with android ever expanding and windows 8 being even greater crap than vista - this would not be something unexpected...

thanks to everyone from ubuntu community!

---

### Post by oldfred on 2012-10-24
Glad that worked for you. :)

---

### Post by nanomac on 2012-11-13
**Re: nVidia GT 525M (Dell Inspiron 15R-N5110) still not working after 12.10!** 			
 			 			 		   		 		 		I do not know  about optimus dual video systems. I think Linus was complaining about  the lack of support from nVidia on optimus systems.

nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Switchable Graphics is killing my Ubuntu Experience - see post #9
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)


Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?pag...tem&px=MTE3MzY]("http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY")

thaaaaaaaaaaaaaank you  Mr Oldfred  I have the same laptop 15r n5110 with nvedia optimus gt525m all things got easy!!! no pain !!
my laptop runing intel test with 57.98 fram/s!!!&optirun test at 120.23 fram/s!!!!!!
wondefull!!
I will do further tests and update ....... thank you Oldfred.. you are  the man !!!!!!

---

### Post by idaneg on 2013-02-10
hi 
this is my first Linux experience
i install Ubuntu 12.10 3 days ago and got inspiron n5110 with GE-force 525m
i did everything that you wrote and i still don't know if my graphic card is working good

how can i check this ?

when i check the graphics tab in the computer info it says graphic driver unknown 

 and my lspci wrote this:
idaneg@idaneg-Inspiron-N5110:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev ff)
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev ff)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
09:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
0b:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

is everything OK ?

Thanks in advance

---

### Post by radiking on 2013-02-14
bumblebee does just this it deactivates nvidia card and u have to use the command optirun to run a program!using pinguyOS 12.04 nvidia has showed their backs to linux users sadly :( i wish they could bring in good support as for windows! there will be not many using windows and many would support opensource

---

