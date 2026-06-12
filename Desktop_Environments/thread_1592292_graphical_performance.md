---
title: "graphical performance"
date: 2010-10-10
forum: Desktop Environments
---

### Post by BartBlackMagic on 2010-10-10
My video adapter: GeForce 8600m GT
Driver: Nvidia 260.19.06
OS: Kubuntu 10.10 (64bit)
My question: How come resizing windows is still so slow (in comparison to Win7 for example), is the cause of the problem the driver, Qt, the linux graphical subsystem,.. and are there plans to improve it?  I'm asking because i notice this since the first release of KDE4 and was wondering whether other people with nvidia graphic cards are having the same problem or maybe have a solution.

---

### Post by schnelle on 2010-10-10
Few tips to improve performance of desktop effects:

1) Go to System Settngs / Desktop effects / All effects and turn off blur effect.
2) Press Alt+F2 and type "oxygen-settings". Under widget style go to animations tab and disable them all. Under window decorations section uncheck "enable animations".

Then restart your system. 

After doing this I got a very smooth desktop effects.

---

### Post by ankspo71 on 2010-10-10
Hi,
You can also do these:

Go to Settings > System Settings > Application Appearance > Style > Fine Tuning. Change the "graphical effects" to "Low Display Resolution And Low CPU" or "High Display Resolution And Low CPU". This makes a big difference on my computer.

Go to Settings > System Settings > Desktop Effects.
Change the "Animation Speed" to "Fast" (or anything faster than "Normal"). That is another one that makes a big difference for me.
In the "All Effects" tab, disable or tweak some of the individual effects.
In the "Advanced" tab, see if enabling "Disable Functionality Checks" makes a difference.

You might also want to consider trying out QtCurve themes. I find them to feel lighter and quicker than the Oxygen themes, even when I use an Aurorae window border. QtCurve is not installed by default so you will need to install it.

Hope this helps.
PS. I use an Nvidia 8400 GS card with the 260 Nvidia driver in 32bit Kubuntu 10.10

---

### Post by BartBlackMagic on 2010-11-17
Changing these things do indeed work (although not yet as wanted)! BUT my system should be capable of running a desktop environment with all bells and graphical effects full open, so the problem is caused by the driver, linux kernel and/or KDE code.  I hope the Wayland display manager (that is going to replace the old and slow X display server in future Ubuntu releases) will improve performance noticeably .

BTW I have some great news! Check this link: [The ~200 Line Linux Kernel Patch That Does Wonders]("http://www.phoronix.com/scan.php?page=article&item=linux_2637_video&num=1") On page 2 there are 2 videos with a demonstration!  The scrolling and window-moving appears much faster, looking forward to a release :)

EDIT: I tried the Liquorix kernel and I feel a noticeable difference in the responsiveness of my system!  Now the only performance hickup is resizing windows... SO SLOW! (with desktop effects disabled it is very fast though)

---

### Post by skag on 2011-06-01
thanks!! :) the windows switching and minimize became significantly faster

---

