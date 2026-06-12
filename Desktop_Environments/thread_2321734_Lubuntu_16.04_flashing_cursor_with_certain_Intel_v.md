---
title: "Lubuntu 16.04 flashing cursor with certain Intel video drivers"
date: 2016-04-24
forum: Desktop Environments
---

### Post by Jam_Holtman on 2016-04-24
This is a Lubuntu specific problem. The problem does not exist on Xubuntu

As is well known Lubuntu is the ideal version for older computers, especially for computer which originally ran XP or were too slow for Windows 7 or 10

I found out that there is an issue with the Intel video drivers, at least certain video drivers in Lubuntu.
I have noticed this already with 4 different "older" which use the Intel  graphics controller series 945 and graphics controller based on the  N455 CPU. Please see screenshots
When booting from the live USB of Lubuntu 16.04 either 32 or 64 bit I get a flashing cursor after a while.
The machine seems to boot but then it stops with a black screen and a flashing cursor in the top left corner.
Xubuntu live USB works perfectly on these machines.
The only way I can get Lubuntu to work on these machines is with the  nomodeset command, but then the graphics doesn't look good and I have no  dual screen support anymore.

Is there anything that can be done about this?

---

### Post by Brent_Santin on 2016-04-24
I can confirm the same problem with a Dell Optiplex GX620 tower which has the Intel 82945G graphics chip on the motherboard.
When I try to use Lubuntu 16.04 from the Live CD (downloaded on the date of this posting - 3 days after release) the boot will stop at a black screen with a flashing cursor in the top left corner and never recover.

---

### Post by jimmynaidoo on 2016-05-01
Had same blank screen with fresh install of Lubuntu 16.04. Discovered that the Intel drivers were not installed. Used Synaptic Package Manager to install 'xserver-xorg-video-intel' and 'xserver-xorg-video-intel-dbg', restarted and all works perfectly now.

---

### Post by ajgreeny on 2016-05-02
Same problem seen here with a rebadged MSI 100U netbook (see thread [http://ubuntuforums.org/showthread.php?t=2322941&p=13481893#post13481893](http://ubuntuforums.org/showthread.php?t=2322941&p=13481893#post13481893))

@jimmynaidoo
How did you manage to install synaptic and those other packages?  Could you get to a desktop at all, as I am having problems even getting a command-line tty console.

I have not yet tried the Xubuntu version but have just downloaded to give it a whirl.

Xubuntu is normally my OS of choice but on this old netbook I think Lubuntu might be faster; that was certainly true of Lubuntu 14.04 which was faster than Xubuntu 14.04.

I'll report back.  I may also try the mini install CD and add Xubuntu-core as suggested by sudodus to see where that gets me.

EDIT:
Just tried the live Xubuntu 16.04 which boots fine and runs as a live system, so that may be an answer, if not my preferred one.

---

### Post by sudodus on 2016-05-02
@ Jan,

Maybe you can install a compressed image file into a USB 3 pendrive in another computer and while there install Xubuntu Core. After that you can try booting your computer (with Intel graphics controller series 945) with the pendrive.

Xubuntu Core is smaller (and lighter?) than the full Xubuntu desktop.

See these links

64-bit system:
[Installation/UEFI-and-BIOS/stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative), dd_text_16.04-UEFI-n-BIOS-4-pendrive-7.8GB.img.xz

32-bit system:
from tarball
[/OBI/Xenial-32-txt](https://help.ubuntu.com/community/OBI/Xenial-32-txt)

can also be installed from a compressed image file from:
[http://phillw.net/isos/linux-tools/compressed-images/](http://phillw.net/isos/linux-tools/compressed-images/), dd_Xenial-32-txt.img.xz (7.8 GB, so should fit in an 8 GB pendrive)

---

### Post by jimmynaidoo on 2016-05-02
> **ajgreeny said:**
> 
@jimmynaidoo
How did you manage to install synaptic and those other packages?  Could you get to a desktop at all, as I am having problems even getting a command-line tty console.



Hold 'right shift' key during boot to access the Grub menu, then press  'e' key to edit the the commands. Locate the words 'quiet splash' on  screen, then use arrow keys to navigate and add the word 'nomodeset'  just after 'quiet splash'(leave a space before and after 'nomodeset'). This will allow the system to boot to a low  resolution desktop. Then use Synaptic to install the drivers.

EDIT: Press 'F10' key after typing 'nomodeset' to boot the system.

---

### Post by Jam_Holtman on 2016-05-04
Thank you. I have converted the installation to Xubuntu and removed Lubuntu.
I used the following sequence of commands:
To convert the existing Lubuntu installation into Xubuntu

**sudo apt-get install xubuntu-desktop**

After that restart

Then on the top left of the login screen choose Xubuntu (you have to start a Xubuntu session)

Then I ran the 2 following commands

**sudo apt-get remove --purge lubuntu-desktop**

**sudo apt-get autoremove --purge**

After that I did a thorough clean-up with Bleachbit, first as normal then also as root.
The machines run well, no problem

After that I upgraded the system from version 15.10 into 16.04

It works well on 2 machines, been running this now for about 3 days.

---

### Post by Jam_Holtman on 2016-05-05
There is another solution which works ((UXA solution)
I used a machine with a working Xubuntu installation for that

I did the following:

Installed Lubuntu on an external hard disk for testing. (I left the Xubuntu on the internal hard disk intact)

Made the **xorg.conf **file**. **saved this file on a separate memory stick
Booted the machine normally with Xubuntu and once booted connected the external hard disk again.
Then I copied the **xorg.conf **filewhere it should be.[B] ( see below)
[/B]I used Krusader in root mode for that

Rebooted the machine now from the hard disk and yes there it worked.


One thing though. The machine did not detect the second monitor, only the default laptop screen was detected.


Source of the information: 

**Old Intel graphics**

 Old Intel graphics may need UXA acceleration instead of the default 
There was this helpful bug report on file at [http://bugs.launchpad.net/ubuntu/+source/linux/+bug/1178982](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/1178982) 
The work-around (Comment #1) was to change the Xorg acceleration method to UXA.  
Work-around: 
Edit (or create) **/etc/X11/xorg.conf** as follows: (there should be a tab before each line except the first and the last). 
Section "Device"
        Identifier "Intel Graphics"
        Driver "intel"
        Option "AccelMethod" "uxa"
EndSectionRestart X (reboot, restart your display manager, whatever). Colors are back to the way they used to be and flash works.

So in other words, I installed Lubuntu 16.04 on a machine with has the problem. I forced the live image (live Iso) to boot using F6 and Nomodeset
I used another working operating system (in this case Xubuntu) to put the **xorg.conf **file where it should be and then the problem is kind of solved (in my case the second monitor was not detected)
This method can also be used when after upgrading from a previous Lubuntu version and there is now a flashing cursor in the top left corner)

---

### Post by sudodus on 2016-05-09
I made a new tarball with a 32-bit Lubuntu system using UXA acceleration. It makes it easier to install Lubuntu in computers with some old graphics chips from Intel, where Lubuntu 16.04 LTS has problems, as described in this thread.

**Lubuntu_16.04_oem-uxa.tar.xz**

It is described at [the following link (in my tutorial thread about the One Button Installer)](http://ubuntuforums.org/showthread.php?t=2172971&page=2&p=13486102#post13486102).

There is a corresponding compressed image file to be installed with [mkusb](https://help.ubuntu.com/community/mkusb),

**dd_Lubuntu_16.04_oem-uxa_2016-may_7.8GB.img.xz** at [http://phillw.net/isos/linux-tools/compressed-images](http://phillw.net/isos/linux-tools/compressed-images)

***Edit:*** This UXA method is only second best. See the next two posts.

---

### Post by Jam_Holtman on 2016-05-10
As we know by now there are three possible solutions to get Lubuntu 16.04 to work with old Intel graphics chips, like **945 series** (Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller 
, or **VGA compatible controller Intel Corporation Atom Processor D4xx**/DSxx/N4xx/NSxx Integrated Graphics Controller), see screenshots in this post, data made with system profiler and benchmark.

There are three possibilities 
1) Nomodeset option. Not very good, graphics don't look good.
2) UXA option. Works, graphics is reasonable, but only one screen available. the second screen doesn't seem to work on my test machine
3) server-xorg-video-intel option. Graphics is the best, performance on playing video was the best.. Also only one screen available.

Tests were performed on an older Lenovo T60 laptop. with T2400 processor, 4 Gig ram
Xubuntu 16.04 on the internal hard disk, Lubuntu 16.04 on the external hard disk

I did two tests, first test I compared the performance with two videos 1280x 720 resolution, one H264 encoded .mp4 and the second a H265 .mp4 encoded video also 1280 x 720
Here are the results.

I did the test with UXA and I uninstalled server-xorg-video-intel (effectively comparing option 2 against option 3

The  cpu load with taskmanager was slightly higher with UXA acceleration on  Gnome Mplayer as well on the H264 as well on the H265 encoded video
However  the video rendering is definitely  less smooth with UXA acceleration on  the H264 video. Especially with a person walking next to a window the  rendering was more jerky. It was clearly noticeable.
On the H265  video on the H265 video the difference was even more. Quite jerky with  an average CPU load of around 55%, before with the xserver-xorg-video-intel the CPU load was around 50%
On  VLC the difference was even worse the H264 which worked a bit jerky  before was now extremely jerky and the H265 video simply got stuck

**Conclusion, from the test results I must say that that xserver-xorg-video-intel gives the best results**

Also I compared on the same machine the performance between Xubuntu 16.04 and Lubuntu 16.04 (same videos as mentioned before).

Two videos tested, H264 encoded .mp4 and H265 encoded .mp4, they are 720p videos 1280 x 720 (encoded with Shotcut)

Lubuntu 16.04 plays both videos fine with the native Gnome Mplayer, both H264 and H265
On VLC only the H264 video plays but jerky, the H265 video doesn't play well at all.

On Xubuntu 16.04 the H264 video plays fine with the native Parole player  
The H265 video plays very jerky with the native Parole player 
On VLC both videos don't play well at all.

**Conclusion: Lubuntu 16.04 with the xserver-xorg-video-intel works better playing movies than Xubuntu 16.04**

---

### Post by sudodus on 2016-05-11
I made a new tarball with a 32-bit Lubuntu system using 'xserver-xorg-video-intel', the best method found in the previous post. It makes it easier to install Lubuntu in computers with some old graphics chips from Intel, where Lubuntu 16.04 LTS has problems, as described in this thread.

**Lubuntu_16.04_oem-intel.tar.xz**

It is described at [the following link (in my tutorial thread about the One Button Installer)](http://ubuntuforums.org/showthread.php?t=2172971&page=2&p=13487384#post13487384).

There is a corresponding compressed image file to be installed with [mkusb](https://help.ubuntu.com/community/mkusb),

**dd_Lubuntu_16.04_oem-intel_2016-may_7.8GB.img.xz** at [http://phillw.net/isos/linux-tools/compressed-images](http://phillw.net/isos/linux-tools/compressed-images)

---

