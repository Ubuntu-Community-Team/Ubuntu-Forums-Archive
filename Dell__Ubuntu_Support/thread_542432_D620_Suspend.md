---
title: "D620 Suspend"
date: 2007-09-03
forum: Dell  Ubuntu Support
---

### Post by ubuntuross on 2007-09-03
HI,

My D620 running Gutsy won't come out of suspend.  It just comes up to a screen with a blinking cursor.  The kernel log, /var/log/kern.log, does not contain anything from it coming out of suspend.  I have to manually hold the power button down for 4 seconds to power it down and then power it back up.

Also, when I press the power button, a popup from the top menu bar says "Action forbidden" Policy timeout is not valid.  Please wait a few seconds and try again.

Does anyone have any ideas, or can tell me how to further investigate this problem?

Thanks.

---

### Post by azvoleff on 2007-09-05
My d620 does almost the same thing. It goes to a black screen with a pointer on resume.  I have to restart it to get it to work.

---

### Post by nick_h on 2007-09-05
Is it just the screen not working when you resume?  Can you suspend from the console?

For debugging read [this](http://ubuntuforums.org/showthread.php?t=505890) thread.
For problems with the screen not working on resume look [here](http://ubuntuforums.org/showthread.php?t=471855).

---

### Post by ubuntuross on 2007-09-05
It wasn't resuming at all.  None of the virtual console would appear, just a blinking cursor with no prompt.  However, I've now updated to all of the latest packages and it is working properly again.

Thanks for your reply.

---

### Post by bimbo on 2007-09-06
If you're using kvm, that's the culprit. Remove kvm modules before suspending or it will always crash upon resume (sure took me a while to find that one).

Also it seems like some Latitudes won't resume when they have been docked since the last boot.

---

### Post by kansei on 2007-09-06
Aha, I see I'm not the only one frustrated using a D620 with Gutsy (using x64 Gutsy here).

I'll have to see if the latest updates fixed it. I primarily use this laptop on campus so it's a major inconvenience to have to shut down every time I want to put the laptop away (to walk to another building for instance). --of course I'm not complaining about this, it's my fault for using a pre-alpha 64-bit linux distro. I have a backup ThinkPad T42 in my car running Feisty 32-bit just in case :P

I figure my issue stems from using the proprietary NVIDIA drivers, but I just haven't gotten a chance to investigate it more yet. I think tonight I'll have time though

*subscribes*

---

### Post by kansei on 2007-09-06
ok here's my report.

I click suspend, and then.. it suspends. Everything seems a-ok there. Hit the power button, it comes back on. bluetooth on, wifi on, hard drive works for a little, then I see the mouse pointer on screen. I can move it around and stuff, but it's like the screen is blanked and the password prompt just won't come. Actually, the keyboard is completely unresponsive. I can't switch virtual terminals, I can't ctrl+alt+backspace to restart x, no ctrl+alt+del, etc. I have to just power off the system.

The wifi even seems to associate (light goes steady)

---

### Post by azvoleff on 2007-09-08
I see exactly the same on my machine.  I have already listed kvm modules to be unloaded prior to suspend, and have played around endlessly with the acpi-default settings, but to no avail.  Everything was working perfectly in gutsy up until some updates a few weeks ago (unfortunately I do not remember the date).

---

### Post by funkadelic on 2007-10-18
I am also having this problem in gutsy final -- black screen after suspend

---

### Post by Starman on 2007-10-18
Welcome to Gutsy...

That has been my only real problem with gutsy since tribe 5. Unfortunately it never got fixed. People spent a great deal of energy trying to blame nvidia or ati or sun spots but no one really had any concrete idea of how to resolve the problem.

I eventually rolled back to feisty where the problem does NOT exist and will wait for this to get sorted out before upgrading.

](*,)

---

### Post by ceronman on 2007-10-23
The same problem for me. My laptop wont resume after suspend. It used to work propertly on fesity. The only good thing is that hibernate now works.

---

### Post by LosD on 2007-10-26
> **ceronman said:**
> The same problem for me. My laptop wont resume after suspend. It used to work propertly on fesity. The only good thing is that hibernate now works.

Suspend works perfectly on my D620 (nVidia) laptop... The funny part is... Hibernate doesn't! :D

By the way, my hibernate problem seems to during the shutdown, as the kernel checks to see if there's a resume image, but doesn't find it, and then starts normally instead.

---

### Post by feranick on 2007-10-26
Maybe this will help.

[bug # 153797]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/153797")

---

### Post by Starman on 2007-10-26
I have confirmed thru repetition that if one performs a clean install of gutsy and does NOT activate the proprietary nvidia driver that suspend does work as expected.

As soon as the proprietary nvidia driver is activated the resume fails when the lid is opened.

So to enable suspend one must sacrifice the increased graphics performance of the proprietary driver...

---

### Post by philipa on 2007-11-10
FWIW, on Feisty I used envy to "upgrade" to nvidia 100.14.23. This broke suspend (or rather, resume).

I reverted to 1.0.9755 (the latest "nvidia-glx-new" from feisty sources), and that corrected the problem.

I conclude that the latest nvidia drivers are indeed the culprit.

---

### Post by jede on 2007-11-18
Suspend 2 Disk (Hibernate) works now for my D620 with the NVidia GFX chip on Ubuntu 7.10 (using the propriatary nvidia-glx-new driver).

I had the same problem as some people here. On suspend the screen goes blank and then nothing happens anymore. I has to power off my laptop manually.

This is a known bug at Nvidia, but this workaround works fine: start an OpenGL application before starting the suspend. I alyways start glxgears before, suspend 2 disk works now very good!

Here's where I found it:
[http://www.nvnews.net/vbulletin/showthread.php?t=93423](http://www.nvnews.net/vbulletin/showthread.php?t=93423)
[http://www.nvnews.net/vbulletin/showthread.php?t=68563&page=6](http://www.nvnews.net/vbulletin/showthread.php?t=68563&page=6)

Does anyone has an idea how to start glxgears automatically before suspend? I don't know where can I add it to a script ...

Bye,
Stefan

---

### Post by bluedragon436 on 2007-11-18
I have a D610 that won't suspend or hibernate on command, but if I leave it sitting by itself running it will eventually go into suspend on its own, the only problem is I can't get it to wake back up without unhooking the power cord, and the battery and then hooking it all back up and restarting the laptop...this gets real annoying.  I have tried everything I can under the power management settings...and it still does it...  HELP!!!!

---

