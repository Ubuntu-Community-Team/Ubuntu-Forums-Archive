---
title: "[SOLVED] NVIDIA Driver installation and X"
date: 2008-03-13
forum: Desktop Effects &amp; Customization
---

### Post by Goldpin on 2008-03-13
I'm trying to install the NVIDIA graphics driver, but when I try to, the program says that X is running and I need to close it.  How do I do that?

Sorry that I'm being so obtuse.

Thanks in advance

---

### Post by Therion on 2008-03-13
Please... Just use [Envy](http://www.albertomilone.com/nvidia_scripts1.html).

---

### Post by Zorael on 2008-03-13
Envy works, but it is an unsupported script.

---

### Post by Nythain on 2008-03-13
envy = not to great... especially for us kubuntu/kde users... went to install it today, and realize it required a lot of gtk apps, and gksu (gnomes graphical sudo equivalent to kdesu), thats just bad form... learn to actually do it instead of relying on a script supported by someone else...

and to answer teh posters question... make sure you are in a tty console (hit control+alt+f1, then log in as yourself, should drop you at a command line prompt)

once you are logged into a tty console type
```

sudo /etc/init.d/gdm stop

```or for kde users
```

sudo /etc/init.d/kdm stop

```should effectively kill x hopefully... you could, alternatively, reboot and at grub quickly hit ESC to bring up the menu and select the same kerne but with (Recovery) after it, wich will log you into the console instead of x

hope that helps

EDIT: Ok, so "sucks" and "wtf" were a bit harsh... i got nothing but respect for the developer/maintainer of the script, its infinately better than anything I can do... im more bitter at its requirements, and the lack of hesitation anyone has as using it as an "end all be all cure for all"... its not that great, it just automates a few simple steps... im also frustrated because what these posters DONT tell you is, when you update your kernel, xorg WILL BREAK... so get used to it... and my last rant, nVidia software is easily installed and configured in ubuntu with no need for Envy... it used to be great back before ATI cards were just as easy to install and set up... i've used it a few times on friends laptops wich have ATI cards installed... just please, for the love of god, stop making it a default answer to anything graphics card/display adapter/xorg related

---

### Post by Goldpin on 2008-03-14
Your advice did the trick.

Thanks

---

### Post by Dylock3 on 2008-03-14
I had the same problem yesterday installing nVidia drivers on my Dell Inspiron e1705.

A driver for nVidia did show up in the restricted drivers window, but it wasn't working.

Here's what I did to install my nVidia driver without using Envy.  Maybe Envy would have worked.  Being a total noob it took me 6 hours of research and trial&error, hopefully this will save some time for some other new uBuntu user.  The below directions work but there is probably a better way to do it.  Also, I did not plan for uninstalling the driver.  If it didn't work, I thought it easier to reinstall uBuntu entirely than try to figure out a work-around for a system with crashed video.  Luckily it worked.

Video card: nVidia GeForce GO 7800

Went to nVidia's Linux driver page for the 7 series video cards
[http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)

Had to install a dependency package from terminal
sudo apt-get install libc6-dev

Then I rebooted and did a terminal session from the login screen (maybe you can do this logged in normally, maybe not)

I had to stop the X System with the following commands
Ctrl+Alt+F1 then
sudo /etc/init.d/gdm stop

...then I could run the nVidia install with this below command.  That is, after I put the file somewhere strange and changed permissions to be totally accessible with the command 'gksudo nautilus'
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run

Success.  Hardest thing I've done with a computer after 5 years of tech support.

---

### Post by Therion on 2008-03-14
> **Zorael said:**
> Envy works, but it is an unsupported script.
You lost me right after the "Envy works" part.

> **Nythain said:**
> … im more bitter at its requirements, and the lack of hesitation anyone has as using it as an "end all be all cure for all"... its not that great, it just automates a few simple steps... im also frustrated because what these posters DONT tell you is, when you update your kernel, xorg WILL BREAK... so get used to it... and my last rant, nVidia software is easily installed and configured in ubuntu with no need for Envy... it used to be great back before ATI cards were just as easy to install and set up... i've used it a few times on friends laptops wich have ATI cards installed... just please, for the love of god, stop making it a default answer to anything graphics card/display adapter/xorg related
Can't help with your bitterness, though it does strike me as a rather extreme response to something as simple as a script.  I don't suggest that Envy is the "End All Be All Fix It Solution of the Gods", I suggest Envy to get a new use over the hump so the first hour they spend with Ubuntu/Linux hopefully doesn't turn into an exercise in frustration and utter bewilderment.

> **Dylock3 said:**
>  Success.  Hardest thing I've done with a computer after 5 years of tech support.
I rest my case.

---

### Post by Zorael on 2008-03-14
> **Therion said:**
> You lost me right after the "Envy works" part.

So you would suggest Joe User won't face "frustration and utter bewilderment" when he boots up his system one day only to be met by a black screen - or at best, a terminal window saying X could not be started? What is this "X" to him? Where would he begin to troubleshoot it? Does he know how to use a terminal? Does his version of X boot up into any form of failsafe mode, or will he assume his Linux installation broke down (since "it's an immature platform anyway" as his friends keep telling him), and then go on to reinstall - or worse yet, revert back to Windows?

If you do manage to get the **official package** installed, the driver won't ever do this. Even if he's told in advance that he'll need to run the script from a terminal, will he remember it in a month? Two months? Perhaps his grandson installed it for him, who is now out of the country.

You're advocating something that in itself installs faster but implicitly requires expertise to recover from, **when** it breaks X. A dirty fix, one that would serve to undermine the inexperienced user when the inevitable kernel update hits. Not to mention that if he'll end up having trouble with the driver later, perhaps from regressions, the larger part of the assisting community here won't have the same driver as him, decreasing his chances of finding help.

Users are free to do as they wish, of course, but I wouldn't advise they step outside of the official repositories until they can handle basic recovery and troubleshooting. Your suggestion assumes too much.

---

### Post by Therion on 2008-03-14
> **Zorael said:**
> So you would suggest Joe User won't face "frustration and utter bewilderment" when he boots up his system one day only to be met by a black screen - or at best, a terminal window saying X could not be started? What is this "X" to him? Where would he begin to troubleshoot it? Does he know how to use a terminal? Does his version of X boot up into any form of failsafe mode, or will he assume his Linux installation broke down (since "it's an immature platform anyway" as his friends keep telling him), and then go on to reinstall - or worse yet, revert back to Windows?
I can tell you that the exact scenario you outline happened to me.  Black screen at boot.  What did I do?  Well the first thing I kind of assumed, was that since Envy got me up and running the first time, that maybe, just maybe it would do it again.  Of course I was staring at a black screen, so what to do in the meantime...  I booted using a LiveCD and asked for help.  I get your point here, and I appreciate it.  We could also "what if..." this until we are both blue in the face.  Is Envy a perfect solution for all people at all times and in every case? No, certainly not.  Will it get a new user up and running so they can at least get their foot in the door and a chance to learn a little something (say for instance about installing video drivers).  It's not as if kernel updates are a daily occurrence.

> **Zorael said:**
> If you do manage to get the **official package** installed, the driver won't ever do this. Even if he's told in advance that he'll need to run the script from a terminal, will he remember it in a month? Two months? Perhaps his grandson installed it for him, who is now out of the country.
I don't know who will remember what, but this isn't attempting to memorize The Rime of the Ancient Mariner.  It's an install script, not rocket science.

> **Zorael said:**
> You're advocating something that in itself installs faster but implicitly requires expertise to recover from, **when** it breaks X. A dirty fix, one that would serve to undermine the inexperienced user when the inevitable kernel update hits. Not to mention that if he'll end up having trouble with the driver later, perhaps from regressions, the larger part of the assisting community here won't have the same driver as him, decreasing his chances of finding help.
Personally I think you're waaaaay over thinking this.  It's a script to install a driver... That's all.  Every time I've had X go nutty of me, whether or not a Kernel update was involved, Envy fixed things.  I'm sorry but I find it hard to argue with the fact that it works for me.

> **Zorael said:**
> Users are free to do as they wish, of course, but I wouldn't advise they step outside of the official repositories until they can handle basic recovery and troubleshooting. Your suggestion assumes too much. 
I both get your point and appreciate your position here.  I just do not agree with it.

In short, I think we are simply going to have to agree to disagree on this one.  No harm, no foul.  Just a difference of opinion.

Cheers!

---

### Post by Zorael on 2008-03-15
Fair enough.

But as my last words: consider the grandfather situation. Not everyone running Ubuntu installed it by themselves, nor do they have the knowledge needed to maintain it. The installer who'd read this thread might lay a trap for the user.

But I agree, neither of us will convince the other of this. :>

---

### Post by lgdahl on 2008-03-17
I have three different computers with NVIDIA graphics cards, one older NVIDIA GeForce FX 5200 AGP, one XFX GeForce 7600GT 256MB PCI-Express and a GeForce 8400M GS 256MB on my laptop.

The cards has been identified correctly by the standard Ubuntu install CD, and the restricted NVIDIA drivers have been recommended for all three cards. Installation of the restricted NVIDIA-drivers has not caused any problems.

A couple of days ago, I wanted to update the drivers. I just deactivated the restricted driver by removing the mark in the dialog box found under «System - Administration», rebooted the computer and then RE-activated the driver again. The new driver then was downloaded and installed, and after another reboot, I was running the latest NVIDIA driver.

Am I the only one not having trouble with installing and updating these drivers? :-)

---

### Post by Dylock3 on 2008-03-17
[QUOTE=lgdahl;4531081Am I the only one not having trouble with installing and updating these drivers? :-)[/QUOTE]

Yes, it seems you are the only one.  I kept checking and unchecking the box but still didn't have 3D capability.

---

