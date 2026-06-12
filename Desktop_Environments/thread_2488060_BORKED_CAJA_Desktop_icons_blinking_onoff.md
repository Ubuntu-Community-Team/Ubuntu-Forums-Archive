---
title: "BORKED CAJA: Desktop icons blinking on/off"
date: 2023-06-21
forum: Desktop Environments
---

### Post by watchpocket on 2023-06-21
This is totally a new one for me:

Caja has been crashing like crazy on me 
(see:[SIZE=1][ Caja v1.26.0-1ubuntu1 frequent crashing on UbuntuMATE 22.04]("https://ubuntuforums.org/showthread.php?t=2487939") below in the index) [/SIZE]
and I can't keep any folder with a PDF or JPG in it open long enough to even copy or move the file.

 So I used the command-line to move a PDF out of its folder and onto  the desktop, when all of a sudden all four of my desktop icons began to  blink on and off, on and off, as if trying to say, "Danger! Danger!" or  "Help Me!"

 What this actually indicates, I have no idea, having never seen such a thing before.

 I'm really hoping someone might know what this means & what to do  about it, because I'm at near-standstill and can't get anything done  with Caja acting so broken.

 All ideas welcome, no matter how strange or off-the-wall they may seem.  *Thanks*.

---

### Post by aljames2 on 2023-06-21
Hi watchpocket

I know you're look for help here and over at MATE for this, hopefully you find a fix soon. I run MATE in a VM and have had no issues w/ Caja, ever.
Have you seen this:  [https://ubuntu-mate.community/t/caja-what-does-this-runtimeerror-mean-exactly/25635](https://ubuntu-mate.community/t/caja-what-does-this-runtimeerror-mean-exactly/25635)

Perhaps an extension issue, or a call for something that isn't installed.

[https://guide.ubuntu-mate.org/#page-caja](https://guide.ubuntu-mate.org/#page-caja)

---

### Post by watchpocket on 2023-06-25
Thanks for your response, aljames2. 

Three things I've tried so far: 

[LIST=1]
[*]I disabled ALL Caja extensions and re-booted. Didn't help. 
[*]I did a complete removal of Caja, re-booted, re-installed Caja and (one-by-one) its accompanying apps and libs. Didn't help. 
[*] I made sure permissions on all files and folders were correct. 
[/LIST]
  The problem is that all I have to do is open a folder that contains a PDF, a JPG or a PNG file, and that folder disappears.
 I don't even get time to try to open the PDF or JPG.

 Still trying to track down the source of the problem.

 Also, as noted above (I only tried this once & I'm not inclined to try again)  when I opened a PDF from the command-line, the icons on my desktop  started to blink on and off. Does this signal something specific?

I wonder if the following has anything to do with this problem:

I have an nvidia driver with an odd version number, as well as one with a version matching my kernel:
```
--> dkms status 
nvidia/535.54.03, 5.19.0-1010-nvidia, x86_64: installed
nvidia/535.54.03, 5.19.0-45-generic, x86_64: installed
```

I've never seen one with a number like "1010" as part of the kernel  version. Do I need both of these?  Should I remove everything with "1010"  in it (see below)?

When I issue this command: 

[I]dpkg -l linux-image-\* linux-headers-\* linux-modules-\* linux-objects-\* linux-signatures-\*'

[/I]I see this (and only hope these are the needed & correct kernel items):```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                    Version               Architecture Description
+++-=======================================-=====================-============-===============================================================
un  linux-headers-3.0                       <none>                <none>       (no description available)
ii  linux-headers-5.19.0-1010-nvidia        5.19.0-1010.10        amd64        Linux kernel headers for version 5.19.0 on 64 bit x86 SMP
ii  linux-headers-5.19.0-45-generic         5.19.0-45.46~22.04.1  amd64        Linux kernel headers for version 5.19.0 on 64 bit x86 SMP
un  linux-headers-686-pae                   <none>                <none>       (no description available)
un  linux-headers-amd64                     <none>                <none>       (no description available)
un  linux-headers-generic                   <none>                <none>       (no description available)
ii  linux-headers-generic-hwe-22.04         5.19.0.45.46~22.04.20 amd64        Generic Linux kernel headers
ii  linux-headers-nvidia-5.19               5.19.0.1010.11        amd64        Nvidia-5.19 Linux kernel headers
ii  linux-image-5.19.0-1010-nvidia          5.19.0-1010.10        amd64        Signed kernel image nvidia
ii  linux-image-5.19.0-45-generic           5.19.0-45.46~22.04.1  amd64        Signed kernel image generic
ii  linux-image-generic-hwe-22.04           5.19.0.45.46~22.04.20 amd64        Generic Linux kernel image
ii  linux-image-nvidia-5.19                 5.19.0.1010.11        amd64        Nvidia-5.19 Linux kernel image
un  linux-image-unsigned-5.19.0-1010-nvidia <none>                <none>       (no description available)
un  linux-image-unsigned-5.19.0-45-generic  <none>                <none>       (no description available)
ii  linux-modules-5.19.0-1010-nvidia        5.19.0-1010.10        amd64        Linux kernel extra modules for version 5.19.0 on 64 bit x86 SMP
un  linux-modules-5.19.0-43-generic         <none>                <none>       (no description available)
ii  linux-modules-5.19.0-45-generic         5.19.0-45.46~22.04.1  amd64        Linux kernel extra modules for version 5.19.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.19.0-1010-nvidia  5.19.0-1010.10        amd64        Linux kernel extra modules for version 5.19.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.19.0-43-generic   5.19.0-43.44~22.04.1  amd64        Linux kernel extra modules for version 5.19.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.19.0-45-generic   5.19.0-45.46~22.04.1  amd64        Linux kernel extra modules for version 5.19.0 on 64 bit x86 SMP

```

My question, then, would be:  Am I perhaps using the wrong nvidia driver which may be causing Caja to crash and causing anomalies like blinking icons?

(Also just noticed that "**22.04.1**" is indicated in the files above, when everything else (inxi, neofetch, hardinfo) tells me I'm on **22.04.2**.)

---

### Post by aljames2 on 2023-06-25
Video could very well be the culprit here.  Looks like you are using the 535 driver, recommended for Windows.  Nvidia website recommends the 470 driver for Linux x64 compatibility.  And, you certainly don’t need two drivers installed.  If it were me, I would explore this avenue further.

---

### Post by #&amp;thj^% on 2023-06-25
> **aljames2 said:**
> Video could very well be the culprit here.  Looks like you are using the 535 driver, recommended for Windows.  Nvidia website recommends the 470 driver for Linux x64 compatibility.  And, you certainly don’t need two drivers installed.  If it were me, I would explore this avenue further.

****
His card will use the 535 driver, but yes those two entries for drivers is puzzling.
Purge all nvidia and install your preferred Driver version if it's not 535 then 530 or 525

---

### Post by watchpocket on 2023-06-25
> [I]the 535 driver, recommended for Windows

[/I]Wow. First I've heard of it. You have any links about this?

Nothing said about windows here: [I][URL="https://www.nvidia.com/download/driverResults.aspx/205464/en-us/"]https://www.nvidia.com/download/driverResults.aspx/205464/en-us/

[/URL][/I]1fallen: Will do.

---

### Post by #&amp;thj^% on 2023-06-25
So far I'm enjoying the 535 driver:
```
apt policy nvidia-driver-535 nvidia-dkms-535
nvidia-driver-535:
  Installed: 535.54.03-0ubuntu0~gpu23.04.1
  Candidate: 535.54.03-0ubuntu0~gpu23.04.1
  Version table:
 *** 535.54.03-0ubuntu0~gpu23.04.1 500
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu lunar/main amd64 Packages
        100 /var/lib/dpkg/status
nvidia-dkms-535:
  Installed: 535.54.03-0ubuntu0~gpu23.04.1
  Candidate: 535.54.03-0ubuntu0~gpu23.04.1
  Version table:
 *** 535.54.03-0ubuntu0~gpu23.04.1 500
        500 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu lunar/main amd64 Packages
        100 /var/lib/dpkg/status

```
watchpocket I wish I had better suggestions, but if it were me I'd purge all nvidia and reboot before installing the driver again.
This is how I always install nVidia on Debian of course also note I use the PPA Driver when possible.
```
sudo apt autoremove --purge nvidia*
```
as you can see I'm not shy for nuking all nvidia related.
```
dkms status 
8812au/5.6.4.2_35491.20191025, 6.2.0-20-generic, x86_64: installed
8812au/5.6.4.2_35491.20191025, 6.2.0-23-generic, x86_64: installed
nvidia/535.54.03, 6.2.0-20-generic, x86_64: installed
nvidia/535.54.03, 6.2.0-23-generic, x86_64: installed

```
Reboot and install:
```
sudo apt insatll nvidia-driver-535 nvidia-dkms-535
```
Would like to hear if this helps your problems.

---

### Post by aljames2 on 2023-06-25
I have a 1030 on 1 Linux machine & APUs on everything else Linux.  I  do have a GTX-1070 on a windows gaming computer, a bit old now though.   I'm behind the times on graphics cards.  Not sure what I was reading on  my iPhone earlier. I recall seeing what seemed to recommend the 470  driver, and references to the 535 were Windows speak. On second look,  with a little more time, and on my 32" monitor, these old eyes clearly  see you indeed can work with the 535, or at least in range of that  driver. Disregard my #4 on this one.  My apologies watchpocket

[https://www.nvidia.com/Download/driverResults.aspx/205464/en-us/](https://www.nvidia.com/Download/driverResults.aspx/205464/en-us/)

Thanks 1fallen for helping straighten the curve on this one :)

---

### Post by watchpocket on 2023-06-25
I got rid of all the "nvidia-1010" stuff.  All I could find on it was: 

**linux-nvidia-5.19-headers-5.19.0-1010**

[I]"This package provides kernel header files for version 5.19.0, for sites  that want the latest kernel headers. Please read  /usr/share/doc/linux-nvidia-5.19-headers-5.19.0-1010/debian.README.gz  for details"

[/I]However that file and last directory was not in my /usr/share/doc/ dir.  The mention of "sites" makes me think it may be for server sites, who knows.

So my driver situation now looks exactly like yours:```
--> apt policy nvidia-driver-535 nvidia-dkms-535                                         
nvidia-driver-535:
  Installed: 535.54.03-0ubuntu0~gpu22.04.1
  Candidate: 535.54.03-0ubuntu0~gpu22.04.1
  Version table:
 *** 535.54.03-0ubuntu0~gpu22.04.1 500
        500 [https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu](https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu) jammy/main amd64 Packages
        100 /var/lib/dpkg/status
nvidia-dkms-535:
  Installed: 535.54.03-0ubuntu0~gpu22.04.1
  Candidate: 535.54.03-0ubuntu0~gpu22.04.1
  Version table:
 *** 535.54.03-0ubuntu0~gpu22.04.1 500
        500 [https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu](https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu) jammy/main amd64 Packages
        100 /var/lib/dpkg/status
-->
-->
--> dkms status 
nvidia/535.54.03, 5.19.0-45-generic, x86_64: installed
-->
```

So I've cleaned up the driver config, but I'm still having the same old Caja crashing when I open most folders. 
Trying to comb through logfiles now.

---

### Post by watchpocket on 2023-06-25
For awhile it did appear that folks were having trouble with anything after nvidia driver 470.  I did not go above that until I installed 22.04.  (I still use 470 on my 20.04 install.) 

535 looks to be working fine for me. I don't think my nvidia driver has anything to do with the Caja crashes.

---

### Post by watchpocket on 2023-07-09
One thing I've discovered is that this problem appears to be NOT  profile-related.  I created a passwordless guest account, and the same  thing happens in that account - if I click on a JPG file, the folder of  JPG files that is open instantly disappears. 

UPDATE:  ***SOLVED***

I went into the File Manager, opened the "Preview" tab, and set everything there to "Never."


 Then, one-by-one, I "un-Never'd".


 The problem is with the *"Other Previewable Files" -> "Show  thumbnails"* setting.[I] [B] If that is set to "Never", the problem goes away.
[/B]
[/I]Since I don't need thumbnail previews, I will now keep the "Show thumbnails" set to "Never."

---

