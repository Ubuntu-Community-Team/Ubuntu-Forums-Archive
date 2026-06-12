---
title: "Black screen on resume in 18.10"
date: 2019-02-06
forum: Desktop Environments
---

### Post by chorca on 2019-02-06
Just updated my Thinkpad T420 up to 18.10 with a fresh install (full wipe). This is a machine with Optimus and I did install prime-select, but only after I was having issues. Otherwise this is a plain system, updated to latest stable updates, with Chrome and Wine installed, but the issues i'm encountering are with nothing running.

The laptop suspends fine, goes fully to sleep with the suspend light on with the system. Upon opening the lid though, I see the monitor blink on for a second with the mouser cursor and then immediately shut off again, the backlight and all turning off.
Pressing ctrl-f1 and then ctrl-f8 shows the console login and then brings me back to the usual XFCE login screen where I can unlock, but without doing that I'm unable to see anything.

Video showing the issue: [https://youtu.be/iFLfiCApCR4](https://youtu.be/iFLfiCApCR4)

Typing my password into the blank screen brings me back to my desktop, so it seems like things in the background are working, but the graphics on the screen are not.
I also tried using prime-switch to test each setting (nvidia and intel) and the same effect happens with each.
I attempted the nouveau.modeset=0 and a couple other fixes in grub, but none of those seemed to have any effect.
The computer is running the latest BIOS afaik.

I haven't seen any bugreports dealing with 18.10 resume issues yet, at least of this type. Anyone else having problems?
Wondering what's the best way to figure out if this is the graphics driver, lightlocker, or something else so that I can open a bug report with the right package.

---

### Post by chorca on 2019-02-23
Still having this issue, haven't seen much of this with the newer version reported..

---

### Post by chorca on 2019-02-24
Noticing that also this seems to happen when the screen is put to sleep by the power manager in Xfce, I have to do a Ctrl-Alt-F7 and then Ctrl-Alt-F8 to get the screen to come back; moving the mouse doesn't seem to help.

Noticed this in dmesg, not sure if this is on resume or when the monitor was slept:
[191724.244393] nouveau 0000:01:00.0: Direct firmware load for nouveau/nvd9_fuc084 failed with error -2
[191724.244410] nouveau 0000:01:00.0: Direct firmware load for nouveau/nvd9_fuc084d failed with error -2
[191724.244414] nouveau 0000:01:00.0: msvld: unable to load firmware data
[191724.244421] nouveau 0000:01:00.0: msvld: init failed, -19

---

### Post by petrako on 2019-04-11
Hi

I'm having the same issue, have you fixed it?

---

### Post by hgkrug1 on 2019-07-18
Have look at the following post - [https://ubuntuforums.org/showthread.php?t=2395562&highlight=suspend+resume+problems](https://ubuntuforums.org/showthread.php?t=2395562&highlight=suspend+resume+problems)

Not sure if it will help?

Best wishes
Gert Kruger

---

### Post by hgkrug1 on 2019-07-18
I have Ubuntu 19.04 installed and experience the same. I can get a terminal with Ctrl+Alt+F1/F3 but subsequent start of the desktop does not work.
 I suspect it may be connected to my Nvidia driver that was installed. I tried the solution provided at [https://www.dell.com/community/Inspiron/Suspend-resume-problems-on-Ubuntu-18-04/td-p/6072410](https://www.dell.com/community/Inspiron/Suspend-resume-problems-on-Ubuntu-18-04/td-p/6072410) (Scroll down to article by 1 Nickel). This refer to a Youtube link ([https://www.youtube.com/watch?v=5nGbWE-pvIE&t=433s](https://www.youtube.com/watch?v=5nGbWE-pvIE&t=433s) ) that enables you to use "bumblebee" to switch between the Intel and Nvidia drivers.
 This can be done from the command line as well:
 $ sudo prime-select intel (sudo prime-select nvidia).
 Solution does not solve my problem, in fact, my PC reverted to a previous issue (blanc screen after installing Nvidia drivers and reboot - see [https://ubuntuforums.org/showthread.php?t=2399985&page=3&p=13861293#post13861293](https://ubuntuforums.org/showthread.php?t=2399985&page=3&p=13861293#post13861293) #23).
 I am yet to see if I can fix that once more.
 Best wishes 
Gert Kruger

---

