---
title: "[HOWTO] 1280 x 800 Resolution on Dell D620 with Intel Video"
date: 2007-08-04
forum: Dell  Ubuntu Support
---

### Post by WillTheComputerGuy on 2007-08-04
So today I reinstalled 7.04 and couldn't get my resolution back to 1280 x 800.  I searched around and tried a few things.  Here are the steps that worked for me.  Steps 1-3 are entered at a console session:

   1. sudo apt-get update
   2. sudo apt-get install xserver-xorg-video-intel
   3. sudo apt-get install 915resolution

Next, close all programs, and press CTRL + SHIFT + ALT + BACKSPACE.  This will restart your Gnome Session.  You should then be presented the log on prompt at the 1280 x 800 resolution.  Alternatively, you could restart your computer.

Comments are welcome.

Original post on my website:
[http://www.willshattuck.com/wp-archives/2007/08/04/ubuntu-704-dell-latitude-d620-intel-video-1280-x-800-resolution/](http://www.willshattuck.com/wp-archives/2007/08/04/ubuntu-704-dell-latitude-d620-intel-video-1280-x-800-resolution/)

Enjoy,
Will the Computer Guy

EDIT: changed xserver line to xserver-xorg-server-intel (TYPO)

---

### Post by walkerk on 2007-08-04
You don't need 915resolution which is a way to change the defualt resolutions while using a driver such as i810. If you are going to use the Intel driver, which your are, all you need is the Intel video driver.

```
sudo apt-get install xserver-xorg-video-intel
```

or if xserver-xorg-intel worked I guess that'll do as well..

---

### Post by davidsiegel on 2007-08-04
Is there any way to get desktop effects working with that driver?

---

### Post by michael37 on 2007-08-05
> **davidsiegel said:**
> Is there any way to get desktop effects working with that driver?

I am not sure.  I typically don't recommend xserver-xorg-video-intel version because it is version 1.9.94 and is not mature yet.  For example, it has fuzziness issues with non-standard resolutions, such as 1280x800 laptop screen.  Wait for Gutsy which will have version 2.0.X.

The "old" tried and true way is xserver-xorg-video-i810 which supports AIGLX and therefore supports Desktop Effects.

---

### Post by WillTheComputerGuy on 2007-08-05
I don't know either.  Like I said above, I don't know of a "proper" way to get it to work, this is just what worked for me.

Personally, I don't care for the desktop effects right now.  Maybe in the future : )

Will

---

### Post by wireddad on 2007-08-18
Will this work with Kubuntu?

---

### Post by davidsiegel on 2007-08-18
> **wireddad said:**
> Will this work with Kubuntu?

Do you mean 915resolution? Yes, it will work with Kubuntu/Edubuntu/etc.

---

### Post by wireddad on 2007-08-18
Yes.  Thank you.  i will try it.

---

### Post by walkerk on 2007-08-18
> **davidsiegel said:**
> Is there any way to get desktop effects working with that driver?

Desktop effects work just fine with the intel driver. I use it without issues.

---

### Post by cbot on 2007-10-07
Hello people,

I have tried this on my dell D620 and when I do any of the apt-get calls for either the 915resolution or the xser-xorg-* I get a message saying that there is no such package on drive E:\

Please note that I have ubuntu installed on a 2GB usb drive.  The process of installing it was basically placing the contents of the live cd on the drive.  You can view the steps I followed [here]("http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install/").
 

Please let me know how I can fix my screen resolution.  Or better yet how I can install full version Linux on a usb drive without modifying my main hard-drive with WinXP (this is my work computer)

I am guessing that apt-get tried to get the package from my flash drive and it is not there.  But I don't really know.

Thank you,
cbot

---

### Post by Linicks on 2007-10-07
> **walkerk said:**
> Desktop effects work just fine with the intel driver. I use it without issues.

Me too.  I installed the intel driver as per the Dell wiki:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Intel_945GM_video_issues](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Intel_945GM_video_issues)

and it works great - I use compiz-fusion and it all works with no problems at all (in fact, it runs perfectly!).

Nick

---

### Post by WillTheComputerGuy on 2007-10-07
Does "apt-get update" work on the USB drive?

---

### Post by Lek130 on 2007-10-16
[http://ubuntuforums.org/showthread.php?t=494943&page=5](http://ubuntuforums.org/showthread.php?t=494943&page=5)

i am not sure you have the same chip set, but do take a look at this thread. its the d630 and 1280x800 on feisty is not issue at all. 

Typcially xrandr should give you the best possible resolution. Anyway take a look at the above, it may work for you.

---

