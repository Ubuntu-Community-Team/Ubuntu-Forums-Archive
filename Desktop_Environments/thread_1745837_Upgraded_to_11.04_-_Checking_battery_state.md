---
title: "Upgraded to 11.04 - Checking battery state"
date: 2011-05-01
forum: Desktop Environments
---

### Post by Hishighness on 2011-05-01
Hey all, I upgraded to 11.04 yesterday but when I try to run it now it freezes on checking battery state.

I've did some looking in the forums and found this post.

[http://ubuntuforums.org/showthread.php?t=1744681](http://ubuntuforums.org/showthread.php?t=1744681)

Which in turn pointed me to this page.

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

I have an ATI Radeon 5450 so I went through the steps for Need to fully remove -fglrx and reinstall -ati from scratch

Now, when I try to start up the screen just goes blank as if I've turned the computer off.

I can run the system in limited graphics mode (or whatever it's called) so I have the ability to do some troubleshooting there, but I'm a Windows convert and am pretty hazy as far as Ubuntu troubleshooting goes so any help would be appreciated. If you need me to run something and post logs or what have you.

Thanks for your time,
H2

---

### Post by Hishighness on 2011-05-01
I forgot to mention I upgraded from 10.10

---

### Post by salterlee on 2011-05-08
Can anyone help PLEEEASE?!! I have this problem too - I can run in low graphics mode (have an nvidia gt9500 card - it won't work with or without the "additional drivers" (it dumps me to a blank desktop - not even panels, just the background).

Please, please please help, this is really not great because I can't use my machine properly and I am also a convert!!!

---

### Post by salterlee on 2011-05-08
Okay, 2 problems, 2 solutions (I hope) - if so please mark as SOLVED.

1. "Checking Battery state" - try changing the graphics driver. I changed versions and it booted (but to blank desktop - see next solution)

2. "Blank desktop" - change desktop to "Ubuntu Classic" (when you got to the login* screen at the bottom of that screen is a taskbar with various options, one of which is the desktop option. I think that the Unity desktop is not only sluggish but also perhaps has compatability problems at this stage. Changing to "classic" sorted my problems. 

*if you have automatic login, you'll need to change this - System > Adminstration > Login screen > show the screen for choosing who will log in.

Hope this helps!!

---

### Post by tez1982 on 2011-05-15
I had the same problem, when booting I either got.....
Checking Battery State [OK]

Then the system just stopped

or
Error: out of disk
grub rescue>

or sometime I just got a blank screen



Solution:
Went into power management and turned off "Spin down hard drives when possible"

I haven't had any problems since - I can only assume for some crazy reason Ubuntu was spinning down my HDD whilst booting??

---

### Post by stevlee on 2011-07-08
I had the same issue after clicking on partial upgrade then reboot on 11.04, then I found this solution and tried and it works !

sudo gedit /etc/default/grub
GRUB_GFXPAYLOAD_LINUX=text
sudo update-grub

then reboot

---

