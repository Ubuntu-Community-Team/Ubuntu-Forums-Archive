---
title: "Getting nvidia to run xserver on debian- HELP"
date: 2007-08-25
forum: Debian
---

### Post by seattle vic on 2007-08-25
I'm a bit new to Linux, so don't know all the processes and sequences of getting nvidia drivers to install correctly, so would "really" appreciate some help.

I have a new pc with an nv 8600 GT installed.  I have vista on the machine and also ubuntu, and they both run it well, at full resolution (1920 x 1200) for my wide screen monitor.  With debian, I've been getting a crash that says it cannot find a driver.

Ubuntu uses the nv driver, and I've tried that as well as nvidia with debian, but with no luck.  I've been wrestling with this for a week.  I've tried to look up everything I can on this and finally tied to substitute vesa for the driver.  That worked, though only gets me to 1280 x 1024.

Today, I took some advice and downloaded the latest nvidia driver (100.14.11) and used the nvidia installer.  It was some progress in that it didn't give me the message that it couldn't find the driver or load xserver.  But the screen was blank.

This shouldn't be that difficult, right?  I've tried several sequences over the last week to get all the modules loaded in the right order, but maybe I need to start over.

I'm extremely frustrated, so some advice, or pointer to the right sequence of events would be appreciated.

Thanks in advance,

Vic

---

### Post by oldlucky on 2007-08-25
> **seattle vic said:**
> I'm a bit new to Linux, so don't know all the processes and sequences of getting nvidia drivers to install correctly, so would "really" appreciate some help.

I have a new pc with an nv 8600 GT installed.  I have vista on the machine and also ubuntu, and they both run it well, at full resolution (1920 x 1200) for my wide screen monitor.  Withdebian, I've been getting a crash that says it cannot find a driver.

Ubuntu uses the nv driver, and I've tried that as well as nvidia with debian, but with no luck.  I've been wrestling with this for a week.  I've tried to look up everything I can on this and finally tied to substitute vesa for the driver.  That worked, though only gets me to 1280 x 1024.

Today, I took some advice and downloaded the latest nvidia driver (100.14.11) and used the nvidia installer.  It was some progress in that it didn't give me the message that it couldn't find the driver or load xserver.  But the screen was blank.

This shouldn't be that difficult, right?  I've tried several sequences over the last week to get all the modules loaded in the right order, but maybe I need to start over.

I'm extremely frustrated, so some advice, or pointer to the right sequence of events would be appreciated.

Thanks in advance,

Vic

If your using Debian Etch this is what i do to install the drivers from Nvidia



Put the nvidia driver into your home directory , set up your sources list with main contrib and non-free example : deb [http://ftp.au.debian.org/debian/](http://ftp.au.debian.org/debian/) etch main contrib non-free

open a command prompt su to root then

1. "apt-get install pkg-config"

2. "apt-get install xserver-xorg-dev"

3. "apt-get install linux-kernel-headers-2.6.18-5-k7" (yours may be different so use uname -r to get your kernel version and substitute it for 2.6.18-5-k7).

4. "apt-get install nvidia-kernel-common"

5. apt-get install gcc-4.1

6.  type "/etc/init.d/gdm stop" "this will take you back to the command line"

log in again as user and then root .

7.type in "export CC=gcc-4.1" hit enter

then type in

8."sh Nvidia-Linux-x86-1.0-8774-pkg1.run --x-module-path=/usr/lib/xorg/modules"

just substitute the "-8774-" for your version of nvidia drivers you have, make sure there is a space between "run and -" and type exactly as above, this will compile the nvidia drivers and walk you through the install , let the nvidia installer write to the xorg.conf file when asked.

When Finished

type, "/etc/init.d/gdm start" then log in as normal and you should have nvidia 3d acceleration.

Cheers

---

### Post by seattle vic on 2007-08-26
> **oldlucky said:**
> If your using Debian Etch this is what i do to install the drivers from Nvidia


Put the nvidia driver into your home directory , set up your sources list with main contrib and non-free example : deb [http://ftp.au.debian.org/debian/](http://ftp.au.debian.org/debian/) etch main contrib non-free

open a command prompt su to root then

1. "apt-get install pkg-config"

2. "apt-get install xserver-xorg-dev"

3. "apt-get install linux-kernel-headers-2.6.18-5-k7" (yours may be different so use uname -r to get your kernel version and substitute it for 2.6.18-5-k7).

4. "apt-get install nvidia-kernel-common"

5. apt-get install gcc-4.1

6.  type "/etc/init.d/gdm stop" "this will take you back to the command line"

log in again as user and then root .

7.type in "export CC=gcc-4.1" hit enter

then type in

8."sh Nvidia-Linux-x86-1.0-8774-pkg1.run --x-module-path=/usr/lib/xorg/modules"

just substitute the "-8774-" for your version of nvidia drivers you have, make sure there is a space between "run and -" and type exactly as above, this will compile the nvidia drivers and walk you through the install , let the nvidia installer write to the xorg.conf file when asked.

When Finished

type, "/etc/init.d/gdm start" then log in as normal and you should have nvidia 3d acceleration.

Cheers

OldLucky,

Thanks for the sequence; that's what I was looking for all in one place.  Unfortunately, I ran though all the steps and got the same result.  Any other ideas???

Vic

---

### Post by seattle vic on 2007-08-26
I thought I'd add my kernel: 2.6.18-4-686, and also that I'm using an nvidia 8600 GT.  I saw some traffic on another forum that people were having an issue with this card.

Vic

---

### Post by oldlucky on 2007-08-26
> **seattle vic said:**
> OldLucky,

Thanks for the sequence; that's what I was looking for all in one place.  Unfortunately, I ran though all the steps and got the same result.  Any other ideas???

Vic

Okay thats strange ,did you get any errors from the nvidia installer  , you are using Etch and not Lenny or Sid , As Lenny at present is broken with the 2.21 kernel using the nvidia installer.

Just run it through again... the installer part i mean,  make sure you log out first  /etc/init.d/gdm stop then log in as root # and run the installer again with  sh NVIDIA-Linux-x86-100.14.11-pkg1.run --x-module-path=/usr/lib/xorg/modules 
this should work fine using Etch unless there is problems with that particular card , it might be worth a google to see if others have had the same issues with that card.

cheers

---

### Post by oldlucky on 2007-08-26
Okay seems as though you are running etch , with that kernel , here is a couple of links to install the driver the Debian way , i am not sure whether the Debian nvidia module will support your card but it may do.

[http://wiki.debian.org/NvidiaGraphicsDrivers#Libraries](http://wiki.debian.org/NvidiaGraphicsDrivers#Libraries)

[http://home.comcast.net/~andrex/Debian-nVidia/installation.html](http://home.comcast.net/~andrex/Debian-nVidia/installation.html)

cheers

---

### Post by oldlucky on 2007-08-26
You will need to get your default resolution for your monitor as well , so grab your monitor book or do a google search to find your Horizsync  +  Vertrefresh  rates.

Now you need to setup your xorg.conf file to use your particular monitor , otherwise it will struggle to get to your desired resolution.

Here is how to do it :  open a terminal and become root ,  then issue this command :  gedit /etc/X11/ xorg.conf

that will open the xorg file , now look for this below and change it to suit your monitor.

Horizsync 28-40 <<<< here
Vertrefresh 43-60 <<<< and here

while your there do the following :

Look for the display section and put your desired screen size  in as follows.

SubSection "Display"
Depth 24
Modes "1920x1200" << put this in front of all  other numbers "1280x1024"	"1024x768" "800x600"	"640x480"
EndSubSection

That will get your monitor ready to use the correct resolution , it wont take place until you restart the x server though.

---

### Post by seattle vic on 2007-08-26
Did all of that.  Went through the procedures again, no issues from the installer, check the ver and horiz refresh (were actually tighter than the monitor allows) and also did have the max resolution, 1920 x 1200.

And yes, I'm using etch.  I was wondering if the kernel could have an issue with the driver.  When I brought up etch, I checked for an updated driver, and this seemed like the right one, but I wonder.

I checked the web and forums and no particular issues came up with the nv 8600 GT  .

I'm getting burned out trying things, so will probably go with the vesa version I've got working for now.  I put in 1600x1200 and the vesa allows that, but not the 1920x1600.

I may plow through the links you sent me in a couple days when I catch back up on my sleep.

Thanks for the advice.

Vic

---

### Post by seattle vic on 2007-08-26
Oh, one last thing on the kernel.  When I was looking for information, I came across some info on dual core processors, which is what I have, and the article referred to a -smp kernel for such a setup.  I'm running 2.6.18-4-686, but I see that there is a 2.6-686-SMP which has a notation of being a transition package, whatever that means.

Think this could be an issue with the nvidia driver??

---

### Post by oldlucky on 2007-08-26
> **seattle vic said:**
> Oh, one last thing on the kernel.  When I was looking for information, I came across some info on dual core processors, which is what I have, and the article referred to a -smp kernel for such a setup.  I'm running 2.6.18-4-686, but I see that there is a 2.6-686-SMP which has a notation of being a transition package, whatever that means.

Think this could be an issue with the nvidia driver??
 
No that's not the problem , i think you will find that smp its supported with your kernel as well , to see if it is run 

 cat /proc/cpuinfo  in a terminal and see if it outputs the 2 cpu's cores


$ cat /proc/cpuinfo
processor       : 0  **<<<<<<<<<<< here**
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
stepping        : 1
cpu MHz         : 1904.060
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc [6]
bogomips        : 3811.22
clflush size    : 64

processor       : 1 **<<<<<<<<<<< and here**
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
stepping        : 1
cpu MHz         : 1904.060
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc [6]
bogomips        : 3808.00
clflush size    : 64

cheers

---

### Post by seattle vic on 2007-08-27
Yes, it recognized both cpu's, same as your example.  Well, back to the troubleshooting...

---

### Post by seattle vic on 2007-08-27
I figured it out, from a post by Rob Dian on 8/7/07, where he inserted a couple lines to delete nvidia residue:

============================
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules*
sudo rm /etc/init.d/nvidia-*

We had to remove everything related to nvidia that comes with default ubuntu/restricted drivers manager. A lot of people don't do this and X will crash or complain about version mismatch.

==============================

That's all it took, and I'm up and working.  I'm so relieved; what a hassle.

Vic

---

### Post by oldlucky on 2007-08-27
> **seattle vic said:**
> I figured it out, from a post by Rob Dian on 8/7/07, where he inserted a couple lines to delete nvidia residue:

============================
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common linux-restricted-modules*
sudo rm /etc/init.d/nvidia-*

We had to remove everything related to nvidia that comes with default ubuntu/restricted drivers manager. A lot of people don't do this and X will crash or complain about version mismatch.

==============================

That's all it took, and I'm up and working.  I'm so relieved; what a hassle.

Vic

Good to see its all fixed now , but i thought you were using Debian not Ubuntu , those instructions i gave your were for Debian Etch not Ubuntu...

Anyway the main thing is its fixed and working correctly.

Cheers

---

### Post by seattle vic on 2007-08-28
Old Lucky,

yes it was for Debian and that's what I was trying to fix.  The Ubuntu advice worked, sans sudo.

It also worked on my Ubuntu system as well.

Vic

---

