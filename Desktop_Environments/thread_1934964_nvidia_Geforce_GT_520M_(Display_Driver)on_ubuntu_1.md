---
title: "nvidia Geforce GT 520M (Display Driver)on ubuntu 11.10"
date: 2012-03-03
forum: Desktop Environments
---

### Post by aithox on 2012-03-03
hello, i have activated my Graphic Driver from " System settings > additional driver " , but my Card is still unknown , after run this command " sudo nvidia-xconfig " .. it boot me in text mode , can u please make a xorg.conf file for me :) HELP! i won't go back to WIN :P

my hardware info :
aspire 4752ZG (acer),
intelR CoreTM B960 processer,
2GB DDR3 Memory
Nvidia GeForce GT 520M

(OOP!! wrong category please Delete THIS i didn't see any delete option)

---

### Post by bogan on 2012-03-03
Hi!,** aithox**,

The 'Additional Hardware' installed driver will not support your Nvidia GT520M card; you need v290.10 or the latest 295.x from Nvidia:  [http://www.geforce.com/Drivers](http://www.geforce.com/Drivers).

Download the .run file, make it executable and run it.

It will create its own xorg.conf file.

If you need more detailed instructions there is a good readme file with the download; or post a request here.

**EDIT:**  BTW: System Info may still show the graphics as "Unknown" even when it is working correctly.

Chao!, **bogan**

---

### Post by Bobhuber on 2012-03-03
> **bogan said:**
> Hi!,** aithox**,

The 'Additional Hardware' installed driver will not support your Nvidia GT520M card; you need v290.10 or the latest 295.x from Nvidia:  [http://www.geforce.com/Drivers](http://www.geforce.com/Drivers).

Chao!, **bogan**
I think the most recent standard drivers for ubuntu are 285.05.09 which should work for his card unless I'm missing something here.

---

### Post by papibe on 2012-03-03
Could you post the result of these commands?
```
lspci -nn | grep -i vga

lshw -C display
```
Regards.

---

### Post by aithox on 2012-03-04
i've tried NVIDIA-Linux-x86-295.20.run from Nvidia.com ..but its failed to boot in GUI

> **bogan said:**
> 
The 'Additional Hardware' installed driver will not support your Nvidia GT520M card; you need v290.10 or the latest 295.x from Nvidia:  [http://www.geforce.com/Drivers](http://www.geforce.com/Drivers).


---

### Post by aithox on 2012-03-04
```

aithox@linuxMint ~ $ lspci -nn | grep -i vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0106] (rev 09)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:0df7] (rev a1)
aithox@linuxMint ~ $ sudo lshw -C display
[sudo] password for aithox: 
  *-display               
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:a2000000-a2ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:2000(size=128) memory:a3000000-a307ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:42 memory:a3400000-a37fffff memory:80000000-8fffffff ioport:3000(size=64)



```> **papibe said:**
> Could you post the result of these commands?
```
lspci -nn | grep -i vga

lshw -C display
```Regards.

---

### Post by bogan on 2012-03-04
Posted by **bobhuber**:>  I think the most recent standard drivers for ubuntu are 285.05.09 which  should work for his card unless I'm missing something here.Nvidia-current, which is what Additional Hardware installs is v 280.13.

500 series Nvidia cards up to 530 require 290.10 minimum, and the latest from nvidia is 950.2 which is required for 550 upwards.

**Posted by MAFoElffen elsewher**e, referring to a similar setup with Intel integrated graphics and nvidia GT555M graphics card:> The Op has two challenges: 

1. The NVidia 550x requires nVidia 295.20 or newer. It is a "new"  chipset. The 290.10 driver that is in the "main" repo's only supports up  to the 530.x chipset. That leaves him with 2 options-

 a) DL and install 295.20 binary from NVidia
 [COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Installing NVidia Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280")**[/SIZE][/COLOR][/SIZE][/COLOR]

 b) Add the Edgers PPA <-- nvidia 295.20 is in the Edger's PPA.  
[Xorg-Edgers PPA]("http://www.ubuntuupdates.org/ppa/xorg-edgers")

Note that 290.20 is not in the "main" repository yet... 

2. That laptop is Optimus (Hybrid Graphics).  Good instructions on  installing Bumblebee there in that previous post... But you still need  to install the NVidia driver first.  The Bumblebee install script then  installs it's scripts, copies the NVidia Xorg.conf file to where it will  copy from when in use.Full text in this Thread: [http://ubuntuforums.org/showthread.php?t=1932392](http://ubuntuforums.org/showthread.php?t=1932392)

I am running a nvidia GT520 with the latest 295.2 driver; previously it ran OK with the 290.10 driver, but would not work properly with the 280.13 from Additional Hardware installation.

Chao!, bogan.

---

### Post by papibe on 2012-03-04
Your have Nvidia [Optimus]("http://www.nvidia.com/object/optimus_technology.html"). Which is a kind of new graphic architecture and it's just starting to be supported on Linux. Despite that fact, there are a couple of projects in progress that have some success to support it.

I would advice you to start reading a couple of useful threads. [This]("http://ubuntuforums.org/showthread.php?t=1657660") one to understand what it is (but a pessimist). And this [other]("http://ubuntuforums.org/showthread.php?t=1845896&highlight=nvidia") one (from post #7), with a more practical approach.

There are laptops that can either disable it, or simplify things by turning off the Nvidia card. Check your BIOS if you have any of those options.

I hope that helps,
Regards.

---

### Post by aithox on 2012-03-05
> **papibe said:**
> Your have Nvidia [Optimus]("http://www.nvidia.com/object/optimus_technology.html"). Which is a kind of new graphic architecture and it's just starting to be supported on Linux. Despite that fact, there are a couple of projects in progress that have some success to support it.

I would advice you to start reading a couple of useful threads. [This]("http://ubuntuforums.org/showthread.php?t=1657660") one to understand what it is (but a pessimist). And this [other]("http://ubuntuforums.org/showthread.php?t=1845896&highlight=nvidia") one (from post #7), with a more practical approach.

There are laptops that can either disable it, or simplify things by turning off the Nvidia card. Check your BIOS if you have any of those options.

I hope that helps,
Regards.

thx for the links.. ! i no nothing about this :)

---

### Post by bogan on 2012-03-05
Hi! **aithox**,

Apart from checking what options your Bios gives for setting/disabling your video cards, it is clear from other threads that some people have had success with the latest version of Bumblebee, others have not, but there do not seem to be other useful options at present.

You can get the latest on Bumblebee here:[COLOR=Blue][http://wiki.ubuntu.com/Bumblebee](http://wiki.ubuntu.com/Bumblebee)[/COLOR]

Good Luck.

Chao!,** bogan.**

---

### Post by aithox on 2012-03-06
> 
The Op has two challenges: 

1. The NVidia 550x requires nVidia 295.20 or newer. It is a "new"   chipset. The 290.10 driver that is in the "main" repo's only supports up   to the 530.x chipset. That leaves him with 2 options-

 a) DL and install 295.20 binary from NVidia
 [COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Installing NVidia Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280")**[/SIZE][/COLOR][/SIZE][/COLOR]

 b) Add the Edgers PPA <-- nvidia 295.20 is in the Edger's PPA.  
[Xorg-Edgers PPA]("http://www.ubuntuupdates.org/ppa/xorg-edgers")

Note that 290.20 is not in the "main" repository yet... 


i haven't tried this yet.. i've 295.20 driver but i don't no how to add the Edgers PPA <-- nvidia 295.20 in the Edger's PPA ... can u give me the code please..

---

### Post by bogan on 2012-03-06
Hi!, **aithox**.
You Posted :> i don't no how to add the Edgers PPA <-- nvidia 295.20 in the Edger's PPA ... can u give me the code please..

Click on the link [Xorg-Edgers PPA]("http://www.ubuntuupdates.org/ppa/xorg-edgers") and follow instructions.

 Chao!,** bogan**

---

### Post by aithox on 2012-03-08
> **bogan said:**
> Hi!, **aithox**.
You Posted :

Click on the link [Xorg-Edgers PPA]("http://www.ubuntuupdates.org/ppa/xorg-edgers") and follow instructions.

 Chao!,** bogan**


i don't no tat which package i should add ... coz there r so many package there...

```

sudo add-apt-repository ppa:xorg-edgers/ppa  sudo apt-get update sudo apt-get install [COLOR=Red]<package name>[/COLOR]


```

---

### Post by bogan on 2012-03-09
Hi!, **aithox**,

You Posted:>  i don't no tat which package i should add ... coz there r so many package there... I agrree there certainly are lots, and I am confused too.

Selecting 'nvidia-graphics-drivers' in the Bookmark or Package list, gives three alternative versions of the nvidia 295.20 driver, for Natty, Oneiric, and Precise, but they are all given the same package name: "nvidia-graphics-drivers".

Apparently distinguished only by the ppa they are downloaded from: xorg-edgers, main, or fresh X crack.

I frankly do not know what to advise you, I only copied the link from MAFoElffen's post, and had not visited the site until I read your latest Post: I expected it to have a Readme file of instructions.

Hopefully he will have a look at this Thread. [ EDIT: I think he intended it as an** alternative** to Downloading from the NVIDIA site, which I gather you have tried, unsuccessfully.]

Have you tried altering the Bios Video settings to de-activate one card?

Or tried the Bumblebee approach?

Chao!, **bogan**.

---

### Post by MAFoElffen on 2012-03-09
> **aithox said:**
> i don't no tat which package i should add ... coz there r so many package there...

Okay. Was asked to jump in and help.

Did you add PPA yet? If not then 
```

sudo add-apt-repository ppa:xorg-edgers/ppa && sudo apt-get update && sudo apt-get upgrade

```Then you need to install your driver... So many ways... I'll tell you the easiest, then an alternate (I can think of 6 ways offhand).

If you have a working XSession, Go to system settings > Additional Drivers... Install nvidia-current-dev (explanation later)

If you only have commandline, 
```

sudo apt-get install nvidia-current-dev_295.20xxx

```X's depending on architecture
 
--OR--
Download one of these files
[nvidia-current-dev_295.20-0ubuntu1~xedgers~oneiric1_amd64.deb]("https://launchpad.net/%7Exorg-edgers/+archive/ppa/+files/nvidia-current-dev_295.20-0ubuntu1%7Exedgers%7Eoneiric1_amd64.deb")
[nvidia-current-dev_295.20-0ubuntu1~xedgers~oneiric1_i386.deb]("https://launchpad.net/%7Exorg-edgers/+archive/ppa/+files/nvidia-current-dev_295.20-0ubuntu1%7Exedgers%7Eoneiric1_i386.deb")
Put them into a directory
```

dkg -i <path to and filename>

```
When you add that PPA is overides your repo source setting for graphics drivers. Nvidia-current-dev_295.20_blah...

Or after adding the PPA, install Synaptic or Aptitude, find the package and install.

Note: If you go with the Edgers PPA (or XSwat for that matter), then went you go doing a distribution upgrade, to say 12.04 LTS next month, then you'll have to do a PPA purge, before you do the distribution upgrade and add it back it afterward. Reason... different PPA repo for each ubuntu version, specialty PPA repo's don't automatically change like main does.

If you downloaded and installed from NVidia's binaries (I have a tutorial on that) you would have to remember that...

To someone that commented: Bumblebee's been around for about a year. There's that and 2+ other alternatives.

---

### Post by punkduck02 on 2012-03-09
I have a nvida GeForce GTS 450 and I'm trying to get dual monitors to work, but for some reason I can only get one of them to show up at a time.  if someone can help that would be great.  I have tried to install the Nvida driver from the web site "NVIDIA-Linux-x86_64-295.20.run" but it wont load, or install. Please help!!

---

### Post by papibe on 2012-03-10
With the spirit and intention that aithox can solve his/her problem ASAP, I just want to remind everybody that this is an system using Optimus (see post #6).

Regards.

---

### Post by 23dornot23d on 2012-03-10
I had similar problems .... my card was the Nvidia 540 with Intel Graphics.

( Hybrid Graphics are not as easy to set up because they switch between the two inbuilt graphics cards to save power apparently )

I solved the problem that I had, with this newer system using the [[COLOR=Blue]_**Ironhide driver**_[/COLOR]]("http://www.martin-juhl.dk/2011/10/moving-to-oneironhide/") .....

The solution is documented in this thread ..... it worked for me ...... and a few others too.

[COLOR=Blue][U][B][http://ubuntuforums.org/showthread.php?t=1871226&page=3](http://ubuntuforums.org/showthread.php?t=1871226&page=3)

[/B][/U][/COLOR]> 

keith@keith-K53SV:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev ff)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
keith@keith-K53SV:~$ date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && /usr/lib/nux/unity_support_test -p && dpkg -s mesa-utils
Sat Mar 10 10:16:02 CET 2012
Ubuntu 11.04
Linux 2.6.38-13-generic
unity 3.8.16
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string:  3.0 Mesa 8.0-devel

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 148
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: amd64
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: [http://mesa3d.sourceforge.net/](http://mesa3d.sourceforge.net/)
keith@keith-K53SV:~$ 



---

### Post by MAFoElffen on 2012-03-10
> **papibe said:**
> With the spirit and intention that aithox can solve his/her problem ASAP, I just want to remind everybody that this is an system using Optimus (see post #6).

Regards.
Between posts #15,18 and bogans earlier post, the OP should have an abundance of info on how to dealt with his his optimus laptop.  In fact he's bee presented with so many options that now it might be difficult for him to decide.

If it where my laptop, I would install the nvidia binary v290.20 and Ironhide.  

I think an explanation between Bumblebee and Ironhide will explain that. Bumblebee came about with all the scripts and such, with the scripts displaying a text menu for execution of other scripts. 

Ironhide started from within the Bumblebee project, then branched out as a separate entity. Ironhide uses the same scripts as it's predecessor, but the menus are GUI (graphical).

Let's see-- graphical or text based of the same program?

---

### Post by aithox on 2012-03-15
hi.. thx q all ... i think i couldn't be completed the instructions you guys showed me .. i tried that but the remaining of downloading hours is about 12Hr blabla .. XD how poor i m ( i m running on 5kb/sec of internet speed ) ...
i've only the binary version of the driver .. i think i've to give up :(

thx q so much...

---

### Post by Barbalras on 2012-03-20
Hi everyone!

Why is this thread marked as "solved"? User aithox just gave up... I have the very same video card (and same issue), I followed all the instructions in the thread and my graphic card it's still not recognized by ubuntu. The last step was to install the nvidia-current-dev package as instructed by 

That means that I cannot get into gnome-shell, it goes to gnome fallback instead. I could only use gnome-shell when I uninstalled all nvidia-related stuff so I was using intel chipset only. Probably I should go back to that option. Anyway, using intel, when I connect an external monitor the image looks blurry so I thought that maybe using nvidia would fix this problem.

I read about the bublebee development but, as I see it, it's only a way to turn the nvidia graphics card off when not needed, so the card should be recognized first, right?

What do you think I should do?
Thank you all

---

### Post by bogan on 2012-03-20
Hi!, **barbalras**,

You Posted:>  I read about the bumblebee development but, as I see it, it's only a way  to turn the nvidia graphics card off when not needed, so the card should  be recognized first, right? As I understand it, both Bumblebee and Ironhide also give the option to force specific programs to use the Nvidia card. whilst saving battery power when it is not needed. 

 But they are not Automatic as Optimus is supposed to be,  workrounds, but less than ideal.

Edit: Whether a Thread is marked 'Solved' or not is a matter for the OP.

Chao!, **boga**n.

---

### Post by Barbalras on 2012-03-20
Hi bogan!

is bumblebee going to help my ubuntu recognize the graphics card?

thanks

pd: apparently [bumblebee 3.0]("http://www.bumblebee-project.org/index.html") is now automatic

---

