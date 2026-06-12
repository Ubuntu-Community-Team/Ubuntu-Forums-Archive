---
title: "No shutdown button. KDM-GDM conflicts..."
date: 2009-12-03
forum: Desktop Environments
---

### Post by cespinal on 2009-12-03
Hello to everyone :) 

Have been trying KDE for the last couple of days-these plasma thingies just lured me in. 

The experience has been however, bittersweet. Performance and usability have been better than I expected, although I couldn't scape some of the most common annoyances we face on gnome, such as the absence of solid video call support on kopete or skype, some video output conflicts and eventual desktop effect crashes. 

Nevertheless, I'm loving it. 

Now, the BIG issue for me here is that the log out menu does not have reboot or shutdown options, moreover, downloading kshutdown wont do the job: It is necessary to log out and shut down from the GDM or even worse for me, use the terminal. 

If I make the switch from GDM to KDM, then the latter crashes X on boot, so It asks me to boot in low graphics mode despite everything looks perfect once I continue on with that option.

I feel I would like to stick with KDE, but this small big issues just have to go!!!! 

How can we solve this??? 

PD: I have both Gnome and KDE installed on Karmic. HPDv9000 with AMD processors and nvidia cards...If that's of any use :P

---

### Post by depeha on 2009-12-03
I've had this problem too. I tried anything, but looks like there's no solution for this... Just reinstalling whole ubuntu (also remove all hidden folders in home)worked for me.
BUT... If you want have both gnome and kde installed, just install kubuntu, then "ubuntu-desktop" and choose KDM as login manger ;)

---

### Post by Zorael on 2009-12-03
Yeah, (the new?) gdm doesn't seem to work real well with KDE.

You say that kdm crashes X? Is anything output to **/var/log/kdm.log** (and/or **Xorg.0.log**)?

---

### Post by cespinal on 2009-12-03
I'm just too lazy to do it all over again :). Having to back up everything and such...guess I'm sticking with just logging out to the gdm screen and shutting down from it. 

Checked logs when the error occurred and did not see anything... but dont trust me..I am still a noob despite being 2 years on this hehe...

Any other workaround for this?

---

### Post by Zorael on 2009-12-03
Raise awareness by making a comment at [the bug report](https://bugs.kde.org/show_bug.cgi?id=214654).

Don't forget to vote for it, too. You get to place 100 votes per product (kdm in this case), and 20 votes per bug. As votes increase hopefully attention to it will, too. (It has 20 votes from me)

---

### Post by Vecho on 2009-12-06
I have similar problem with kde and x crash too.

---

### Post by Zorael on 2009-12-06
Again, when X crashes and there's nothing that indicates why in **/var/log/Xorg.0.log** (which is otherwise the first place to look), have a look at **/var/log/kdm.log**. It sometimes contains stuff that Xorg.0.log doesn't.

As an anecdote, I had X crash on me some time back (during Karmic development), and Xorg.0.log said nothing. kdm.log however showed error output suggesting a missing symbol in <path>/intel_drv.so. This led me to downgrade the intel driver, and the crashes stopped.

---

### Post by cespinal on 2009-12-07
oh well... I suppose I keep it like this until Im 10000% sure I want to stick with KDE..Then make a fresh install of kubuntu.

---

### Post by Vecho on 2009-12-07
First sorry for my bad english :)
I don't know if this is useful, because I am new to ubuntu.
I did some  research and found something interesting in /var/log/Xorg.0.log:

(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1400x1050"x0.0  108.00  1400 1448 1560 1688  1050 1053 1057 1066 -hsync -vsync (64.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Printing probed modes for output LVDS1

ubuntu 9.10 with kubuntu-desktop and default desktop manager kdm. When I switch back to gdm prblem disappears. My laptop hp nc6320 should use 1400x1050 and 60 hz. 

P.S. Problem looks similar to [this]("http://ubuntuforums.org/showthread.php?t=1348436").

---

### Post by Jetro on 2011-05-02
> **Vecho said:**
> First sorry for my bad english :)
I don't know if this is useful, because I am new to ubuntu.
I did some  research and found something interesting in /var/log/Xorg.0.log:

[snip]

ubuntu 9.10 with kubuntu-desktop and default desktop manager kdm. When I switch back to gdm prblem disappears. My laptop hp nc6320 should use 1400x1050 and 60 hz. 

P.S. Problem looks similar to [this]("http://ubuntuforums.org/showthread.php?t=1348436").
That's funny, because you seem to have the EXACT opposite of what's causing the problem for the rest of us – namely that using KDM *fixes* the problem. :p .After all, you posted in this thread even though I don't understand much of your post. Anyway, I will go [here]("http://ubuntuforums.org/showthread.php?t=1318983") and link to this.

---

### Post by bergfly on 2011-05-03
For the shut-down option, Have you allowed shut down for your users in the system settings?

Open system settings, scroll down to system administration, then look for the start-up and shut-down icon. Click on that. Then go to session management and make sure offer shut-down options is checked.

---

