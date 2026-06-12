---
title: "Runaway vertical scrolling in Ubuntu 11.04"
date: 2011-10-28
forum: Desktop Environments
---

### Post by sethtriggs on 2011-10-28
I've had this issue before but now this is a different style. I rather think I might have an angle as to what has caused this.

First of all, by runaway vertical scrolling, I mean that whenever any window is opened and I touch the scrollbar with my mouse, the window automatically scrolls to the bottom. This is especially killer to the launcher ribbon on the left side of the desktop. I have to right-click an entry to launch it to have any success, and I must have lightning-fast reflexes.

I cannot find anything that governs the scrolling behavior and I don't know how to check whether something is constantly sending "scroll down" inputs to the computer. This happens with different mice no matter if they're plugged in PS/2 or USB. I have a Wacom tablet, I've unplugged that and tried the mouse, no joy.

I'm using an NVidia 6200 AGP card, which leads me to my angle.

In order to successfully use the NVidia 6200 card, there must be an Xorg.conf.

However, an xorg.conf seems to conflict with the new peripheral handling with HAL. As an example the generated (and "working") Xorg has an entry for the mouse and keyboard. I am almost getting this to work except for this stupid mouse scrolling issue.

So the thrust of my question is:

Is there a way to reconcile this apparent conflict between HAL and Xorg? I'm able to use Unity now, so the NVidia driver can be used, but it's just not playing nice with my pointing devices!

Thanks in advance,

-Seth

---

### Post by Favux on 2011-10-28
Hi sethtriggs,

The Nvidia installer shouldn't be adding keyboard and mouse stuff to your xorg.conf.  Just the video stuff.  That's Nvidia's fault for providing a dated installer.  Comment out those sections and any line they have in "ServerLayout" to test.  You shouldn't need them, and if so you can then remove them.  Don't know if that will help with your issue though.

By the way HAL/.fdi files are no more.  Starting with Lucid (10.04) it's xorg.conf.d/.conf files.

---

### Post by sethtriggs on 2011-10-28
Ahhh okay! I will try that! At one point I removed instead of commented out the mouse and keyboard settings. Do you mean for the "Input Device" areas and not the Mouse and Keyboard entries in the "Server Layout" section?

I had noticed the conf.d/.fdi files and for some reason thought those were due to HAL (since they have individual devices now instead of everything in one file.

Thank you so much!

-Seth

---

### Post by Favux on 2011-10-28
> Do you mean for the "Input Device" areas and not the Mouse and Keyboard entries in the "Server Layout" section?
I meant both.  You may not even need a "Server Layout" for the video sections depending on the release etc.  Just test by commenting out and once you've verified you don't need it delete it.

They (Debian/Ubuntu) cheated in Lucid.  Because it has Xserver 1.7 it should support HAL/.fdi but they backported an early version of Xserver 1.8 to get rid of HAL as quickly as possible.  So the Lucid Xserver 1.7 is a hybrid.  That's why it only has the one xorg.conf.d in /usr/lib/X11 instead of the standard location of /usr/share/X11.  And you can't put in user defined .conf files in a xorg.conf.d in /etc/X11 because the hybrid doesn't support that location.  It all gets straightened out with X server 1.8.

---

### Post by sethtriggs on 2011-10-28
> **Favux said:**
> I meant both.  You may not even need a "Server Layout" for the video sections depending on the release etc.  Just test by commenting out and once you've verified you don't need it delete it.

They (Debian/Ubuntu) cheated in Lucid.  Because it has Xserver 1.7 it should support HAL/.fdi but they backported an early version of Xserver 1.8 to get rid of HAL as quickly as possible.  So the Lucid Xserver 1.7 is a hybrid.  That's why it only has the one xorg.conf.d in /usr/lib/X11 instead of the standard location of /usr/share/X11.  And you can't put in user defined .conf files in a xorg.conf.d in /etc/X11 because the hybrid doesn't support that location.  It all gets straightened out with X server 1.8.

Okay I tried commenting out the Input device sections but maybe I should try that again. will see if I can comment out server layout and Input Device, see what happens.

My InputDevice lines under ServerLayout are the following:


InputDevice     "Keyboard0" "CoreKeyboard"
InputDevice     "Mouse0" "CorePointer"

Interestingly the Mouse0 Input device has the device as "/dev/psaux" and there's a "Z Axis Mapping" Option going on with that, saying "4 5"

-Seth

---

### Post by sethtriggs on 2011-10-28
No joy - I commented out the Input Device sections in both Server Layout and the standalone Input Devices in /etc/X11/xorg.conf - the mouse is still scrolling down uncontrollably. Something is making the mouse keep giving down-scroll events!

I do note that when I didn't have an Xorg.conf the mouse worked just fine, but that also meant that the NVidia card couldn't be used. I had to ditch an ATI card for this issue, and the only AGP graphics card left was an NVidia. So I am rather stuck here, to put it lightly.

Ubuntuforums is unbrowseable due to this issue on the system in question, so I can't even send the xorg or the mouse.conf files.

Is there any utility that can detect problems with the system's handling of pointing devices or no? I realize I have a pretty unique situation here.

-Seth

---

### Post by Favux on 2011-10-28
Well mouse in System Settings or wherever it is should have some stuff.

That doesn't make much sense.  Is there any chance your mouse went bad, with the scroll wheel stuck at scroll down?  Have you tried another mouse or that mouse on another system?  Or that mouse in another OS?

---

### Post by sethtriggs on 2011-10-28
> **Favux said:**
> Well mouse in System Settings or wherever it is should have some stuff.

That doesn't make much sense.  Is there any chance your mouse went bad, with the scroll wheel stuck at scroll down?  Have you tried another mouse or that mouse on another system?  Or that mouse in another OS?

I tried different mice on this and different computers - the mice work just fine. It's just that something is sending a downwards scroll effect. On top of that it looks like I have to use a right-click to get the ribbon to stop moving when I want to click something. Same with menus at the top- I have to right-click to activate them. My 11.04 installation is working perfectly on the Gateway laptop as it always does, and that was upgraded several systems over time.

-Seth

---

### Post by sethtriggs on 2011-10-28
My computer works! The issue seems to have been the joystick connected - I have a Microsoft Precision Sidewinder joystick and it seems to have failed. So I disconneected it and the scroll issue went away.

Thank you! This troubleshooting seems to have helped me figure out how all this really works.

-Seth

---

### Post by Favux on 2011-10-28
Great!  Nice job.  :)

I was going to say something seemed to be sending a Button press (scroll down) without a release and hardware seemed the likely culprit.

---

### Post by 05c4r1t0 on 2011-12-17
Hi

I've the same problem. My Ubuntu 11.04 was installed one month ago and this work good!
But today, I connected my USB Drive (WD My Passport) and Ubuntu moved the vertical scrollbar at the bottom of any window o browser page. Even, when i click in the option located at the right top of Ubuntu (Gear Icon), the cursor move at the last option.

Now, i can't see correctly any web page, file browser or any stuff that have vertical scrollbar or menu.

My laptop is HP Pavilion dv9000, Intel Centrino Duo and NVidia Geforce 7600.

---

