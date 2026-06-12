---
title: "Dell Dimension 2350 *ubuntu 10.04 strange video issues"
date: 2010-05-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by intok on 2010-05-03
Hello, I've been getting these issues with the video on this Dimension 2350 [http://support.dell.com/support/edocs/systems/dim2350/specs.htm#1101572]("http://support.dell.com/support/edocs/systems/dim2350/specs.htm#1101572")

So first its 2 issues that may somehow be related, the first and most glaring one is a random video crash that leaves the screen flashing on and off displaying black and white lines down the top 1/3rd of the screen, after quite some time the Ubuntu vesa error screen comes up, selecting the "run in low graphics mode" just leaves me with a black screen, forcing me to shutdown, but oddly the proper Ubuntu shutdown screen displays when I shut down via the power button without hard resetting.

This crash is repeatable on both Ubuntu and Xubuntu 10.04 on this same machine, it seems to happen if any 3d is detected form more then about 5 seconds as tested with the searchlight ant screen saver as well as can be triggered by selecting any resolution higher then 960x529.

The 2nd error is that while at the login screen I can see the mouse cursor, but at login, the display flashes for a second then returns, but does not display the mouse when loaded to the desktop. The mouse cursor is still active though as I can still pick up were the mouse is as it highlights what it's over and can still click on things, this state remains till the screen saver (blank screen) is activated, after which the cursor displays normally.

Below are glx info and xorg.conf etc.

[http://pastebin.com/mfvx2g2Z]("http://pastebin.com/mfvx2g2Z")

[http://pastebin.com/T2cdJxdT]("http://pastebin.com/T2cdJxdT")

[http://pastebin.com/dG0KBR0V]("http://pastebin.com/dG0KBR0V")

[http://pastebin.com/YAe8bvzV]("http://pastebin.com/YAe8bvzV")

---

### Post by jtbse on 2010-05-05
Sorry I don't have a solution for you, but just replying to say I've experienced both of those same symptoms with 10.04 on my Dimension 2400....which also uses the on-board Intel graphics.

The first issue with the video crash only happened a couple of times right after I installed, while I was fiddling around with trying to figure out how to get RhythmBox to import music from an smb share.  It hasn't happened sense.  I wasn't too concerned because I've just ordered a new PCI video card for the machine.  But it sounds like you have some better data points on this than I do.

The second issue with the mouse happened to me just today....but I thought it was just because I was doing some "odd" things.  I had just rebooted the machine remotely from a ssh shell, and had to switch my kvm to the ubuntu system to get to the main console.  When the desktop came up, the mouse pointer disappeared in exactly the way you describe.  A reboot solved the problem.

So...I'm guessing there's some flaky things going on with the Intel Extreme 3D Graphics on these machines.

---

### Post by jvin248 on 2010-05-07
I'm finding the same issue with 10.04

I've been running this Dell Dimension 2350 (and Gateway VX900 monitor) on (xubuntu) 8.04, 7.10, and 6.06.  Been a good workhorse office machine.  The on-board intel video has always been a problem though. Up through 8.04 I've had to modify the Grub boot line to ensure 'nomce' is included or else no video on boot.  That doesn't seem to do anything on 10.04.

Trying to upgrade to 10.04 (and checked 9.10 now too) and they flash screens many times and 'almost' settle in.  10.04 released version is better than beta1 and 2 as those never got the to desktop. When the desktop did show, moving the mouse made it start rechecking resolutions again - flashing.

Appears to be Xorg related as this machine has the same issue with OpenSuse 11.2.  However PCLiuxOS 2010 LXDE boots fine, so maybe Gnome is involved too.

Where are the new graphics card and monitor settings kept on 10.04? I know they tried to get auto-configuring improved, but I'll need to put in a manual fix.

edit.. just tried Xubuntu 9.04 and it loads fine (as precaution I included 'nomce' on the F6 boot options).

---

### Post by UKBB on 2010-05-07
I have a Dimension 4600 that had problems with the on board video as well. Not as bad as what you describe but it was definitely lacking. I went and got a cheap eGeForce card and that took care of it. If you have an open pci card give it a try. You can get them for under $40.

[http://www.amazon.com/EVGA-e-GeForce-5200-128-GPU/dp/tech-data/B0001XX0PS/ref=de_a_smtd](http://www.amazon.com/EVGA-e-GeForce-5200-128-GPU/dp/tech-data/B0001XX0PS/ref=de_a_smtd)

---

### Post by oyok2112 on 2010-05-08
Seems like quite a few people are having trouble with Intel 8xx graphics as well:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes")

Hopefully that will help.

---

### Post by bensteph on 2010-05-15
Has this problem been fixed yet for Ubuntu 10.04?  I had the same problem with the flashing lines on the screen every so often, so I installed Ubuntu 9.10.

---

### Post by 2roombas on 2010-05-17
I've had these very same problems on my Dell Dimension 2350 too. I have tried ubuntu, xubuntu, kubuntu, and lubuntu. I've tried the betas, as well as the final releases, and I just cannot go any higher then 9.04 without experiencing problems.

I tried this below from that above given link, which **claims** to be a workaround.

[INDENT]1) At the purple screen with a keyboard and stickfigure, press Enter to get to the menu.
2) Hit Enter to select your language, and then press F6 and then Esc.
3) Add "i915.modeset=1" after "quiet splash".
4) Press Enter to boot the LiveCD.[/INDENT]

I thought it actually worked too, bc my computer was working fine for several hours, then...  boom!... crash, flicker and flash. Sigh.:(

---

### Post by errold32 on 2010-12-27
see official solution if desired (it is the same as below)
[http://askubuntu.com/questions/8143/is-ubuntu-10-04s-blank-screen-blinking-with-white-stripes-problem-resolved-in](http://askubuntu.com/questions/8143/is-ubuntu-10-04s-blank-screen-blinking-with-white-stripes-problem-resolved-in)

After having to figure this out a second time for another computer, I thought i'd better write it down here.

for Ubuntu 10.04 LTS

to fix the white stripes problem, install the patch below
this works for (some?) of the 8XX series of intel ingrated graphics cards, the 82845G/GL [BROOKDALE-G] in my case.

steps 

1) sudo add-apt-repository ppa:glasen/855gm-fix

2) sudo apt-get update

3) sudo apt-get upgrade 

4) sudo apt-get install 855gm-fix-dkms

5) reboot

This fixes the flashing white stripe issue, as well as glitches like intermittent white blocks, or green lines etc on boot.


sources:
(english section)
[http://www.glasen-hardt.de/?p=959](http://www.glasen-hardt.de/?p=959)

[http://www.dacs.org/forum/viewtopic.php?f=12&t=222](http://www.dacs.org/forum/viewtopic.php?f=12&t=222)

---

