---
title: "Problem with NVIDIA driver"
date: 2009-04-08
forum: General Help
---

### Post by QpSmiley on 2009-04-08
Okay so I just installed Ubuntu and I'm trying to get the NVIDIA drivers but when i get 180 it gave me this error
```

(EE)NVIDIA(0): Failed to initialize the NVIDIA graphics device
PC|:0:13:0
(EE)NVIDIA(0):      Please see the COMMON PROBLEMS
section in the README for
(EE)NVIDIA(0):      additional information
(EE)NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) Screen(S) found, but none have a usable configuration

```

and then i tried version 173 of the driver and it gave the same error on start up after that i can click Ok and it askes

What Would You Like to do?
-Run Ubuntu in low-graphics mode for ju(i cant read after that)
-Reconfigure graphics
-Troubleshoot this error

... I tried running it in low graphics and it comes up but ... in low graphics mode obviously I don't want that haha.
Can anyone help me I didn't see any errors like mine when I searched but if you can point me to a direction to another topic I will be eternally grateful... thanks Ubuntu Forum!

EDIT: btw running ubuntu 8.10
Processor: AMD Atholn 64 x2 Dual Core Processor 5600+ 2.8 GHz
RAM:3072MB
HD:500GB
Graphic Card: NVIDIA GeForce 6150SE nForce 430

---

### Post by cariboo on 2009-04-08
I would suggest you start in recovery mode, and at the menu select xfix, once it is finished select resume and continue on to your desktop. This should start you up with the default video driver. Open System-->Administration-->Synaptic Package Manager and remove all mention of nvidia. Next make sure you are fully upgraded before installing the restricted drivers.

Jim

---

### Post by jim.bauer10 on 2009-04-08
I am having the same problem, except I used Wubi and now it just brings me to the GRUB4DOS prompt, and the bootloader can't find any of its files.

I have no idea how a driver install erased my GRUB information.  Could the fact that I'm using Wubi have something to do with it?

My setup is for all intents and purposes the same as his, except for the fact that I'm running an 8500GT and an Intel.

EDIT:  How would I go about starting in recovery mode?  I can't even boot past the GRUB prompt.  I think maybe my problem is a little worse than his.  Not to hijack the thread.

---

### Post by QpSmiley on 2009-04-08
sorry to ask but how do i start in recovery mode?

---

### Post by sadicote on 2009-04-08
If you don't see the boot menu options it would seem that you have have not yet updated immediately after installation. Why don't you go to update manager and update first?

---

### Post by QpSmiley on 2009-04-08
okay thanks I did what i was told from cariboo and installed the 180 again and i got the same result ...

I recovered it...
then I removed any mention of NVIDIA
then I updated
then I reinstalled 180 
then I rebooted 
Same Error what should I do now?

---

### Post by jim.bauer10 on 2009-04-08
How would I go about getting to update manager?

---

### Post by QpSmiley on 2009-04-08
administration-> update manager

---

### Post by sadicote on 2009-04-08
System>>Administration>>Update Manager

---

### Post by sadicote on 2009-04-08
QpSmiley, you beat me to the draw there. Try this, remove all mention from Synaptic again, go to terminal and type "sudo apt-get install nvidia-glx-180", then do a "sudo apt-get update". After that type "sudo nvidia-xconfig". Do not include the quotation marks. Reboot after that. If that doesn't work, then we would have to wait for the real experts to take over.

Sorry, missed looking at your system specs.

---

### Post by QpSmiley on 2009-04-08
Well You didnt say to run recovery so I didnt but I followed ur instructions and I'm getting the same error
Time to wait for the pros i guess unless i was supposed to run recovery

---

### Post by sadicote on 2009-04-08
Yeah i guess so, no harm in trying recovery though.

---

### Post by QpSmiley on 2009-04-08
ran recovery and now in the terminal after i wrote "sudo nvidia-xconfig"
it returned

VALIDATION ERROR: Data incomplete in file /etc/x11/xorg.conf Device section " Configured Video Device" must have a Driver line.

Backed up file 'etc/x11/xorg.conf' as '/etc/x11/xorg.conf.backup'
New X configuration file written to 'etc/x11/xorg.conf'
... reboooting now ill tell u how it goes

EDIT: New Error!(i dont know if i should be excited or worried)
same erros as original but it nows stars with 
(EE) Failed to load module "type 1"(module does not exist,0)

---

### Post by QpSmiley on 2009-04-08
bump (if allowed)

---

### Post by jim.bauer10 on 2009-04-09
I figured out my problem.

Apparently God no longer wants me to have Ubuntu, because my entire Wubi file just up and disappeared.  I used a utility to find deleted and corrupted files which found files that I had formatted over 6 years ago, but not the Ubuntu file.  The drive reports that the file is still taking up space but I can't find it for the life of me.  This is more trouble than it's worth.  How did a driver install cause this?

And in response to a previous post, I am entire unable to get past the GRUB prompt so Update Manager and Recovery are obviously not options.

---

### Post by sadicote on 2009-04-09
It would seem that your nvidia-glx-180 got removed. Verify this in Synaptic, and if true install it again with sudo apt-get install nvidia-glx-180 nvidia-settings,and then do the sudo nvidia-xconfig. Reboot is needed after this. Ignore the error message after sudo nvidia-xconfig and don't go for the recovery mode this time. Please understand that i don't know much more than you do, i have just been lucky enough to get my Nvidia drivers in with the few commands that i suggested, every time (yes, even after they crashed once before, then again when i had to reinstall them after an upgrade to a new kernel) Since you have just installed, might i suggest a reinstall and immediate update if the above doesn't help?

Be sure to remove all nvidia related items from Synaptic before you do the sudo apt-get install nvidia-glx-180 nvidia-settings.

there is a space between nvidia-glx-180 and nvidia-settings

---

### Post by QpSmiley on 2009-04-09
that solution doesn't work ... same error starting now with 

(EE) Failed to load module "type 1"(modules does not exist, 0)

---

### Post by QpSmiley on 2009-04-09
Good Morning Ubuntu Forum this is a BUMP =D

---

### Post by QpSmiley on 2009-04-09
darn I'm on the second page ... bump

---

### Post by QpSmiley on 2009-04-09
bumpity bump bump

---

### Post by ashour on 2009-04-09
I just had this problem few ours ago just choose go back to default configuration then open up ubuntu then open a terminal and type

sudo apt-get update
sudo apt-get upgrade

after that open System >> Adminstration >> Hardware drivers and pick 177 or 173 i think the problem that 6xxx series card aren't supported anymore by nVidia updates or at least that what i think not sure of it (they just show 8 series and higer on their website).

---

### Post by fazza on 2009-04-09
tut tut you shouldn't do that :p (sorry I was talking to QpSmiley)
I do though

I've had much the same problem as you, but it seems to be the newer build of 180 because I've already had it installed and running fine.
However, I cannot fix my graphics at the moment because I uninstalled my broken kernels (all of them) and they won't reinstall (lol fits well).
So if I reboot, I can't do anything anyway :S
[Here]("http://ubuntuforums.org/showthread.php?t=1120306")'s my kernel post

---

### Post by QpSmiley on 2009-04-09
> **ashour said:**
> I just had this problem few ours ago just choose go back to default configuration then open up ubuntu then open a terminal and type

sudo apt-get update
sudo apt-get upgrade

after that open System >> Adminstration >> Hardware drivers and pick 177 or 173 i think the problem that 6xxx series card aren't supported anymore by nVidia updates or at least that what i think not sure of it (they just show 8 series and higer on their website).

now it doesnt show that i have any proprietary drivers =/

---

### Post by QpSmiley on 2009-04-09
2nd page bump!

---

### Post by fazza on 2009-04-09
great well it just got worse... I know I can install them from synaptic, but I'm sure there's an issue when the hardware drivers manager doesn't show anything at all... Just a blank window. Great.

(btw I got the kernel sorted)

---

### Post by QpSmiley on 2009-04-09
bump

---

### Post by QpSmiley on 2009-04-09
Okay so i reinstalled ubuntu and tried the following drivers

180
177
173
96

none of them worked same error as original ... any other suggestions?

---

### Post by norwoods on 2009-04-09
type 1 is a font collection that you do not need, you can just delete the line containing type 1 from xorg.conf or rename xorg.conf(so you can go back to it if you need to)and create a new one with sudo nvidia-xconfig.  nvidia-xconfig may complain about missng things but will create them as necessary.

---

### Post by QpSmiley on 2009-04-09
> **norwoods said:**
> type 1 is a font collection that you do not need, you can just delete the line containing type 1 from xorg.conf or rename xorg.conf(so you can go back to it if you need to)and create a new one with sudo nvidia-xconfig.  nvidia-xconfig may complain about missng things but will create them as necessary.

That went away when I reinstalled ubuntu

(01:25:21 PM) KindPersononIRC: Are you still around?
(01:25:40 PM) KindPersononIRC: Looking at your X-server log, it looks like your problem is with the GLX extension.
(01:25:55 PM) KindPersononIRC: NV driver is running, however it can't initialize the GLX
(01:26:05 PM) KindPersononIRC:  [http://pastebin.ubuntu.com/147698/](http://pastebin.ubuntu.com/147698/) Line 645:  (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not
(01:26:07 PM) KindPersononIRC: +found)

---

### Post by QpSmiley on 2009-04-09
bump

---

### Post by fazza on 2009-04-09
mine is very similar...:

Failed to initialize nvidia kernel modul! Please ensure that there is a supported nvidia gpu in this system, and that the nvidia device files have been created properl. Consult the nvidia readme.
Screens found but non have usable configuration.

then it drops to low graphics mode. I ran nvidia-xconfig, and compared the files - there was an obvious difference. Then, on guesswork, I ran modprobe nvidia. returned nothing, but didn't return an error either.

looking in synaptic, nvidia-180-kernel-source, nvidia-settings, nvidia-xconfig, nvidia-180-modaliases and xserver-xorg-video-nv are installed. But not nvidia-glx-180, which seems to be quite necessary. However, I can't install this because it conflicts with nvidia-xconfig, and if I haven't got that installed then I can't configure the graphics anyway.

This is beyond stupid... unless there's another option. I have nvidia-glx-new (which doesn't conflict with nvidia-sconfig) listed, but it has no installation candidate, so won't work anyway.

WHAT THE HELL?!

---

### Post by QpSmiley on 2009-04-09
mine is saying nvidia-glx-new doesnt exist =/

---

### Post by QpSmiley on 2009-04-09
bump and lspci
```

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6150SE nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
01:06.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)

```

Log:
[http://pastebin.ubuntu.com/147698/](http://pastebin.ubuntu.com/147698/)

---

### Post by QpSmiley on 2009-04-09
I missed being on the front page and its still not fixed.... oh btw i foudn out i need the 173 driver btu im still getting the error 

Bumpsky

---

### Post by fazza on 2009-04-09
yeah, I've tried 180 and 177, but now jockey works. I've also tried envy. Either way, they both break the graphics driver :S

---

### Post by norwoods on 2009-04-09
System-->Administration-->Hardware Drivers with the 185.13 driver lists the GeForce 6150SE nForce 430 as supported.  use synaptic to install the 185.13 driver.  if you dont get 180 driver running after a reboot, run System-->Administration-->Hardware Drivers where you should see the 180 driver. Deactivate any active driver,then Activate the 180 driver and reboot.

---

### Post by fazza on 2009-04-09
none of these programs work... in my case at least, it would appear to be a kernel-related issue. All the graphics interfaces are built from the kernel (I think), and none of my kernel images will install properly.

Also, I do not have 185 listed; it only goes as far as 180 in both envy, synaptic and jockey.

any ideas on that?

---

### Post by SlackAttack on 2009-04-09
I have the same problems I have a 8800 GT and I can't get anything to work.  I have treid 3923859383529823 possible solutions and they all fail.   Someone with more skill then me needs to write a script that automates some of these "fixes".

---

### Post by fazza on 2009-04-09
well for an however many years old necessity, and such an advanced branch of linux, I'm kinda surprised we still get major issues such as this. I know it's all constantly being worked on and changed etc, it just seems strange.

---

### Post by fazza on 2009-04-09
update: got the kernel sorted out, but the graphics driver still won't work. So they're not related.

---

### Post by collinp on 2009-04-09
Hmm, not sure what your problem is. We are fine over here in Jaunty, have you tried removing nvidia-xconfig then installing nvidia-glx-180? If you do, nvidia-glx-180 should install the needed dependencies along with itself.

---

### Post by fazza on 2009-04-09
ahh sorry I just bumped it then saw your message :p

er yeash I have tried that... it does install everything it needs, it's just when i reboot and it still falls back to low graphics mode after yelling at me.
And I'm in the middle of coursework and exams... NOT the time to upgrade to Jaunty!
Out of interest, how smoothly does the jaunty upgrade go?

---

### Post by fazza on 2009-04-09
actual bump this time

because I would really really like my compiz back soon
as would most people on this thread :p
cheers

---

### Post by sadicote on 2009-04-10
What can i say, i am so sorry...

OK, one last shot..maybe your chipset cannot handle compiz, try removing it, i have even though i didn't need to because i need all the memory i can get for my Blender and other graphics intensive applications.

---

### Post by fazza on 2009-04-10
naa it's worked since I got it. I have nVidia 8600 GT, with 1GB of DDR3 ram on it. I think that can handle compiz!
I've just tried the whole process again this morning, and still it won't work. Short of editing the configs by hand, I think I've tried pretty much every path now :(
Thanks anyway :)

---

### Post by Thura on 2009-04-10
I have that prob twice before.
First time, I solved by reinstalling it ... 
For the second time, I did a couple of things, and it is solved, but I really don't which solved the problem ...
here is a couple of things that I did ...

Uninstall every nvidia-related packages, download and install the latest official package [here.]("http://www.nvidia.com/object/linux_display_ia32_180.44.html")

According to Xorg [Faq]("http://www.x.org/wiki/FAQErrorMessages#head-83b2f9b8c18db15e641ed9e0be8f9a8364001e5b"), so I modified xorg.conf manually ...

```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
##  Modified the modes and depths manually, according Xorg error info
    SubSection     "Display"
        Depth       8
        Modes      "1400x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1400x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1400x900" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       32
        Modes      "1400x900" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by sadicote on 2009-04-10
Linuxbasics.org is where i used to go before i began to feel comfortable in the Ubuntu forums. Try this link to see if you can extract something useful out of the exchange [http://linuxbasics.org/forum/index.php?topic=358.0](http://linuxbasics.org/forum/index.php?topic=358.0). If nothing works then i can only repeat my suggestion of a reinstall.

---

### Post by norwoods on 2009-04-10
> **fazza said:**
> naa it's worked since I got it. I have nVidia 8600 GT, with 1GB of DDR3 ram on it. I think that can handle compiz!
I've just tried the whole process again this morning, and still it won't work. Short of editing the configs by hand, I think I've tried pretty much every path now :(
Thanks anyway :)
how about trying to remove any cruft with the following:
sudo envy --uninstall-all 
sudo dpkg -P envy 
sudo apt-get remove --purge nvidia*
sudo rm /lib/restricted-modules/.nvidia*
sudo nvidia-installer --uninstall

preparing for install with:
sudo apt-get install build-essential linux-headers-`uname -r`

i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.44 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev

---

### Post by VotaVader on 2009-04-14
I did it!! :guitar: I had the exact same problem and I just figured out how to solve it. Maybe you guys figured it out already since the thread has been untouched for a couple of days, but I'll post it just the same for future reference.

I noticed that when I tried to install the driver and sources through Synaptic (after completely removing and all that), it seemed to install fine, but if I expanded the details, in the terminal there was the following error:
```
Error! Your kernel source for kernel 2.6.27-11-generic cannot be found at /lib/modules/2.6.24-21-generic/build or /lib/modules/2.6.24-21-generic/source.
Installing initial module

Error! Could not locate nvidia.ko for module nvidia in the DKMS tree.
You must run a dkms build for kernel 2.6.27-11-generic (i686) first.
Done.
```
or
```
Error! Bad return status for module build on kernel: 2.6.27-11-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia/180.11/build/ for more information.
Installing initial module

Error! Could not locate nvidia.ko for module nvidia in the DKMS tree.
You must run a dkms build for kernel 2.6.27-11-generic (i686) first.
Done.
```
So I figured it wasn't building the driver module correctly. I googled around a bit, trying everything in half the internet's forums to make it work XD.
Finally it came down to 3 things:
1) Make sure you're building the driver for the appropriate kernel. If the kernel number given in the error is not the same as the one you're using, try updating your menu.lst (had to do that first, it was still pointing to Hardy).
2) Reinstalling the header files for the kernel. I'm not sure if this was necessary because I tried 2) and 3) together, and not independently, so I'm not sure which of the two solved the issue. To reinstall the header files, go to Synaptic, search "linux headers" and _completely remove_ all the packages that start with linux-headers, then reinstall them.
3) After completely removing all nvidia drivers (specifically nvidia-180-kernel-source, nvidia-glx-180, and nvidia-settings), run the following code:
```
sudo apt-get install dkms 
```
This should set up DKMS correctly before installing the drivers. Now install the drivers, and they should build properly.

Now, I'm assuming you guys have a similar problem because I had the exact same errors that you're talking about.
Just in case, some other errors I bumped into along the way were while I was trying to fix the driver, and if someone still has trouble, we might be able to figure it out by trying these things:
1) Trying to manually build the driver module, gave an error something like this:
```
pedro@pedro-laptop:~$ sudo dkms build -m nvidia -v 180.11 -k $(uname -r)

Preparing kernel 2.6.27-11-generic for module build:
(This is not compiling a kernel, just preparing kernel symbols)
Storing current .config to be restored when complete
Running Generic preparation routine
make mrproper.......
using /lib/modules/2.6.27-11-generic/build/.config
(I hope this is the correct config for this kernel)
make oldconfig......
make prepare-all.....(bad exit status: 2)

Building module:
cleaning build area....
make KERNELRELEASE=2.6.24-21-generic module KERNDIR=/lib/modules/2.6.24-21-generic IGNORE_XEN_PRESENCE=1 IGNORE_CC_MISMATCH=1 SYSSRC=/lib/modules/2.6.27-11-generic/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.27-11-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia/180.11/build/ for more information.
0
0
```
Your result might be a bit different because this is from when I had the version problem too, but it's almost the same when fixed.
2) The make.log file in /var/lib/dkms/nvidia/180.11/build/ read something like this:
```
DKMS make.log for nvidia-180.11 for kernel 2.6.27-11-generic (i686)
dom ott 5 10:15:18 CEST 2009
If you are using a Linux 2.4 kernel, please make sure
you either have configured kernel sources matching your
kernel or the correct set of kernel headers installed
on your system.

If you are using a Linux 2.6 kernel, please make sure
you have configured kernel sources matching your kernel
installed on your system. If you specified a separate
output directory using either the "KBUILD_OUTPUT" or
the "O" KBUILD parameter, make sure to specify this
directory with the SYSOUT environment variable or with
the equivalent nvidia-installer command line option.

Depending on where and how the kernel sources (or the
kernel headers) were installed, you may need to specify
their location with the SYSSRC environment variable or
the equivalent nvidia-installer command line option.

*** Unable to determine the target kernel version. ***

make: *** [select_makefile] Error 1
```

I hope this helps someone, and if you keep having problems maybe some of it might point you in the right direction. Cheers! ):P

---

### Post by Elios modual on 2009-04-24
well i got a nvidia driver and i'm using my default what exactly do i have to do to upgrade and where do i go in the system to do it?

---

### Post by Thura on 2009-04-24
Just go to synaptic ... then search for "nvidia-glx" ... then you will see like ...
nvidia-glx-96, nvidia-glx-173, nvidia-glx-180 ... choose the one with greatest number (i.e. , nvidia-glx-188 ) and install

---

