---
title: "Dell Latitude E6510 - Ubuntu 10.10 installation problems"
date: 2011-01-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by didadi777 on 2011-01-20
Hi folks,

I bought a refurb E6510 recently and I want to install Ubuntu 10.10 (preferred) or 10.4. THere have been numerous posts online regarding the black screen during bootup and even I have experienced the same. Dell / Ubuntu doesn't seem to really bother about fixing the intel drivers nor there is any adequate information online. Ubuntu site tells the users to go and check with Dell for the free installation CD (10.04 i believe) but Dell is not ready to send one to me. (They say purchase is required,which is stupid).

Has anybody succesfully installed Ubuntu 10.10 (or 10.04  for that matter, on E6510? (Mine is i5/Intel HD graphics). If yes, can you please list the instructions or any tricks that were used. (Hitting F6, nomodeset etc did not work so far :(

Your help is appreciated..Thanks

---

### Post by b18turboef on 2011-01-21
I'm sitting here on my E6510 wondering the same thing. Love the laptop, and got a screaming deal on it, but sure not enjoying being forced to use win7. Any help or input would be appreciated everyone!!

---

### Post by didadi777 on 2011-01-22
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453)

This is the bug we are hitting.I installed older kernel and it works like charm..(some minor quirks),but better than having blank screen. 

2.6.36-rc4 is what is needed. Hopefully community (*WE*) will straighten this out. I'll try to do some testing as required by the patches that might come up.

Cheers

---

### Post by b18turboef on 2011-01-25
> **didadi777 said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453)
 
This is the bug we are hitting.I installed older kernel and it works like charm..(some minor quirks),but better than having blank screen. 
 
2.6.36-rc4 is what is needed. Hopefully community (*WE*) will straighten this out. I'll try to do some testing as required by the patches that might come up.
 
Cheers
 
Missed your post because I forgot to check the email me button haha....
 
I havent clicked the link, and will after posting this, but how do I change the kernel? I've already installed 10.10 but have the black screen issue... tried a million things but not that. I need like an "change your kernel to 2.6.36-rc4 for idiots" thing haha!

---

### Post by hawthornso23 on 2011-01-27
I've installed 10.10 on my E6510. There are instructions around for getting past the black screen issue. They do work. 

I'm happy very with it. Most of the hardware works just fine. WIFI is fine. Networking is fine. Keyboard is recognised. Sound is fine. Camera and Microphone work fine. However expect to have to deal with some minor issues.

ISSUE: The Touchpad isn't recognised as such. Ubuntu identifies it as a PS2 mouse. It functions just fine as a pointing device (including tap to click), but advanced touchpad functions (eg touchpad scrolling) are unavailable. The biggest  annoyance is with the lack of 'disable as you type'. 

WORKAROUND: I set up a couple of keyboard shortcuts to disable/enable  the touchpad. There are also suggested fixes around which are supposed to enable the touchpad to be correctly identified and to restore some ALS touchpad functionality. However my understanding is that none of these fully fixes the problem. I haven't tried them as I'm happy with the workaround (and I mostly plug in a mouse anyway).

ISSUE: Suspend/resume works however sometimes fan control stops working after a resume. Reboot to get your fan back if you end up in this state else you'll be running hot. This bug was supposed to have been fixed (it has been closed out on launchpad), but I still seem to suffer sporadically from the problem. 

WORKAROUND: Via power control select the hibernate or shut down options instead of suspend in all cases. Be aware of the state of your fan and reboot if it stops working.


These are the main issues I've found, although I haven't tested some of the weirder hardware options (fingerprint reader?) available on this machine.

---

### Post by didadi777 on 2011-01-28
For 10.10, can u pls tell me the exact steps that you followed to get past the initial boot screen? I did use the nomodeset but no success.

I'm using i915 (integrated chipset) and what I've read is this works for Nvidia chipsets and not the Intel integrated ones. As told earlier, the intel-drm-next upstream kernel seems to have fixed this issue and I've tested it. I'm just interested in knowing 10.10 - whats the fix because my other virtualbox etc depends on the stock kernel.  Your help is appreciated.

---

### Post by hawthornso23 on 2011-01-29
My E6510 has both intel onboard graphics and the nvidea 3100 nvs. Sorry, it seems I didn't read your original post carefully enough. Are you saying yours doesn't have the nvidea card? If so then we are in different worlds.


As I understand it BOTH graphics chipsets fail to work out of the box for completely different reasons leading to a black screen. 

1. The intel onboard graphics has some issue that apparently requires a kernel fix.[URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453"]
https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453[/URL]

2. The nouveau (free) driver installed by default for the nvidea 3100 nvs has a completely different problem and also fails to work. I havn't looked into the details of this problem too deeply because the proprietary driver DOES work. So getting a functional machine is simply a matter of telling it not to use nouveau, which can be done with 
```
nouveau.modeset=0
``` 
from the grub menu. That will get you into a functional state from which you can install the proprietary driver. 

If you only have the intel graphics, then I understand from what I have read that "xforcevesa" will allow you to boot into terrible vesa graphics so you can work on the problem. A fix involves messing around with your kernel. 

Good Luck.

---

### Post by didadi777 on 2011-01-31
"messing" with kernel. That is what exactly I've said on the post. There is a bug that has been fixed and either needs a patched kernel or use a pre-built RC kernel as said above and use it. Thanks for ur time.

---

### Post by ajmctaggart on 2011-01-31
Hey everyone,

I too have the E6510 i5 with Nvidia...

Here's the deal...

Has anyone just pressed the "S" for skip when they've been on the straight black screen?  I seem to remember that actually working (may have been CrunchBang Linux though).

This post (specifically this post's kernel recommendations does indeed help...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625")

Post#248

Good Luck!

---

### Post by venmx on 2011-04-04
FYI - I've just had this same problem with a Latitude E6510 and Intel graphics.

**Symptoms:** Blank screens during install.

**Solution:**

[LIST=1]
[*]Boot from CD.
[*]Hit any key when you see a small keyboard and person in the centre/bottom of the screen.
[*]Select keyboard layout.
[*]Use up/down arrow keys to highlight (don't select) "Install Ubuntu".
[*]Press **F6**; you will see a pop-up menu and behind it the string of kernel boot options.
[*]Press **ESC** to exit the menu, then **TAB** to place the cursor at the end of the line.
[*]After the "--" enter: **nomodeset xforcevesa**; this will allow the OS to continue to install with video, but when you next restart the problem will reoccur.
[*]To get around this, when the system restarts hold down **SHIFT** to enter the GRUB boot screen.
[*]Press "**e**" to edit the GRUB boot options, then enter the same text as before (**nomodeset xforcevesa**) at the end of the line that begins with "linux /boot/vmlinuz".
[*]**CTRL+x** should continue to boot the system successfully.
[*]But to make this change stick, you must edit the file "/etc/default/grub" in the Terminal enter: **sudo nano /etc/default/grub**
[*]Then enter the same text as before (**nomodeset xforcevesa**) after "quiet splash", so the line looks like: **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset xforcevesa"**
[*]Save and exit.
[*]Then in the Terminal, enter: **sudo update-grub**
[/LIST]
The system should now boot without any video issues. Thanks to Dell Premier Support team for working closely with me and providing the fix :)

---

