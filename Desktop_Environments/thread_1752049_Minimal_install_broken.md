---
title: "Minimal install broken"
date: 2011-05-07
forum: Desktop Environments
---

### Post by MooPi on 2011-05-07
Amid all the Unity bashing threads, the fact that the minimal install is  broken seems to have been lost in the volume of noise. This is an issue  near and dear to me because all of my installs in the past have been  minimal builds. Has anyone been able to get the minimal install CD to  function ? Once I got 11.04 installed and all the Gnome of consequence  removed I had a similar install to what I'm used to but not the same :(   . 
Basically I'm using an Openbox desktop that is quite lean in setup and  the removal (Gnome) process leaves alot to be desired. To much cruft  left behind, or to much left behind that I'm afraid to remove for fear  of breaking the install. Looking for feedback or news that someone has been able to get the minimal CD to work.

---

### Post by mikewhatever on 2011-05-07
What exactly is broken in the minimal install? Were there any problems with installing the command line base system? Why did you install the ubuntu-desktop in the first place?

---

### Post by MooPi on 2011-05-07
The minimal install will not boot after completion. There is no prompt just a blank screen and sometimes the monitor just gives no signal response. To get a somewhat working environment I had to boot to grub and root console to install xdm and openbox. After restart I boot to find folder and file permissions screwed up and overall functionality a mess. So I used the full install then compaired my install base from previous 10.10 Openbox install to the new full 11.04 unity(using dpkg --get-selections) install so I can remove and change my DE.

---

### Post by mikewhatever on 2011-05-07
Hope that will be fixed shortly. Meanwhile, you could try the command line system installation from an Alternate CD.

---

### Post by MooPi on 2011-05-07
Same result sadly.

---

### Post by mikewhatever on 2011-05-07
That's odd. Any bug reports on this?

---

### Post by gatewayasteroid on 2011-05-10
> **MooPi said:**
> Amid all the Unity bashing threads, the fact that the minimal install is  broken seems to have been lost in the volume of noise. This is an issue  near and dear to me because all of my installs in the past have been  minimal builds. Has anyone been able to get the minimal install CD to  function ? Once I got 11.04 installed and all the Gnome of consequence  removed I had a similar install to what I'm used to but not the same :(   . 
Basically I'm using an Openbox desktop that is quite lean in setup and  the removal (Gnome) process leaves alot to be desired. To much cruft  left behind, or to much left behind that I'm afraid to remove for fear  of breaking the install. Looking for feedback or news that someone has been able to get the minimal CD to work.

I installed a minimal system using the alternate CD. Then I put xorg, openbox, tint2, conky, wbar, pcmanfm, ...

Everything went fine, except:

- xorg didn't get my screen resolution (1366x768, maverick did it perfectly). I had to run gtf and add an xrandr to my startup script

- alsa didn't work: I had to create a simple .asoundrc file in my home dir and to add my user to the audio group

- pcmanfm and thunar couldn't mount any external drive: I had to edit /usr/share/polkit-1/actions/org.freedesktop.udisks.policy

- gphoto2 and gtkam do not work. I gave up.

---

### Post by CarpKing on 2011-05-27
I had this problem too.  Ctrl+Alt+F1 should get you to a commandline.  See this bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/761830](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/761830)

---

### Post by wildmanne39 on 2011-05-27
> **MooPi said:**
> Amid all the Unity bashing threads, the fact that the minimal install is  broken seems to have been lost in the volume of noise. This is an issue  near and dear to me because all of my installs in the past have been  minimal builds. Has anyone been able to get the minimal install CD to  function ? Once I got 11.04 installed and all the Gnome of consequence  removed I had a similar install to what I'm used to but not the same :(   . 
Basically I'm using an Openbox desktop that is quite lean in setup and  the removal (Gnome) process leaves alot to be desired. To much cruft  left behind, or to much left behind that I'm afraid to remove for fear  of breaking the install. Looking for feedback or news that someone has been able to get the minimal CD to work.
Hi, I did a minimal install a few weeks ago and it work great no problems. I did not do anything special it was my first minimal install with ubuntu,I have done one with gentoo in the past, ubuntu is all most automatic compared to that.

---

### Post by MooPi on 2011-06-15
> **CarpKing said:**
> I had this problem too.  Ctrl+Alt+F1 should get you to a commandline.  See this bug: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/761830](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/761830)

Thanks for the info and will attempt a fresh install today testing the Ctrl+Alt+F1 solution. Read the bug report and seems this bug is pervasive and not entirely fixed as yet. Keep the feedback coming and any news on a fix. 

Performed the install today. Everything went smooth except for one small detail, my sound is fubar'd. 

Sound is fixed. For some reason I was not part of the audio group and didn't have sound card privileges, weird right ?
Now my last bug to fix is the auto mount or hot plug of usb and external drives.

---

### Post by MooPi on 2011-06-21
Has anyone else got everything working on their minimal installs ?

---

### Post by gatewayasteroid on 2011-06-26
> **MooPi said:**
> Thanks for the info and will attempt a fresh install today testing the Ctrl+Alt+F1 solution. Read the bug report and seems this bug is pervasive and not entirely fixed as yet. Keep the feedback coming and any news on a fix. 

Performed the install today. Everything went smooth except for one small detail, my sound is fubar'd. 

Sound is fixed. For some reason I was not part of the audio group and didn't have sound card privileges, weird right ?
Now my last bug to fix is the auto mount or hot plug of usb and external drives.

Nobody should part of the audio group:
[https://wiki.ubuntu.com/Audio/TheAudioGroup](https://wiki.ubuntu.com/Audio/TheAudioGroup)
A solution is to use a login manager (like lxdm). It manages all the consolekit/policykit stuff and so you'll have the right privileges (audio, mounting, ...). It worked for me.

---

### Post by MooPi on 2011-06-29
> **gatewayasteroid said:**
> Nobody should part of the audio group:
[https://wiki.ubuntu.com/Audio/TheAudioGroup](https://wiki.ubuntu.com/Audio/TheAudioGroup)
A solution is to use a login manager (like lxdm). It manages all the consolekit/policykit stuff and so you'll have the right privileges (audio, mounting, ...). It worked for me.
Okay I took this info and installed jackd2 and pulseaudio and removed myself from the audio group only to loose sound again. I am using a login manager as well, (xdm). I have since reverted to the original config of my system to enable sound. Any other suggestions would be welcome.

---

### Post by gatewayasteroid on 2011-07-31
> **MooPi said:**
> Okay I took this info and installed jackd2 and pulseaudio and removed myself from the audio group only to loose sound again. I am using a login manager as well, (xdm). I have since reverted to the original config of my system to enable sound. Any other suggestions would be welcome.

Did you try LXDM as a login manager? It worked with me, even if I'm using Express Linux now ;)

---

