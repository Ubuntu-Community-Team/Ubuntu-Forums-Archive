---
title: "Title bars disappeared and other window manager breakage"
date: 2011-05-23
forum: Desktop Environments
---

### Post by gaz514 on 2011-05-23
Hi all,

I came into work this morning to find XFCE's window manager completely broken: no title bars, unable to move windows around, and unable to focus on a window to type in it (terminal, browser address bar, etc.). I tried going into the preferences then window manager settings, but just got a blank panel. Deleting .config/xfce4 didn't solve the problem.

Any ideas? I'm thinking of just doing a clean install of Xubuntu, or more likely another Xfce-based distro, since my current setup (regular Ubuntu with Xubuntu also installed) is quite messed up (same startup applications being used for Gnome and Xfce, and various other issues). I can't remember whether I did any updates last Friday that might have broken it.

Interestingly I used to have similar issues with Xmonad when I used it - some features didn't work properly and I had to restart the WM to fix them. Never did find a proper solution.

Thanks.

---

### Post by Copper Bezel on 2011-05-23
Is the window manager broken, or just not running? Try running xfwm4 --replace. If that brings it back, then you can set it as a startup application (which, as you say, would also mean that Gnome would use XFWM) or save the session for future logins with the XFCE session manager (something that seems simpler but which I don't have any real experience with.)

---

### Post by koen.lefever on 2011-07-09
I have the same problem: no window borders, the "Window Manager" screen in the Settings Manager is empty, I cannot increase the number of workspaces (it jumps to one single workspace), text fields cannot get focus (well, the field I'm typing in now has the focus, everything I try to type into Synaptic or Xterm appears in this field on my browser - the scrollbars and menus in Synaptic however can get focus), other windows in the background cannot get focus...

Just before this happened, I installed "Goobox" and "asunder" with their dependencies from Synaptic, which asked me to restart my computer. After the install the WM was unusable. Uninstalling Goobox and asunder did not revert the situation.

I tried the "xfwm4 --replace" as suggested in the above mail, but that did not help, got error "(xfwm4:2069) GTK Warning: cannot open display."

---

### Post by Toz on 2011-07-09
From one of the xfce developers: [http://forum.xfce.org/viewtopic.php?id=6102]("http://forum.xfce.org/viewtopic.php?id=6102")

---

### Post by koen.lefever on 2011-07-09
> **Toz said:**
> From one of the xfce developers: [http://forum.xfce.org/viewtopic.php?id=6102]("http://forum.xfce.org/viewtopic.php?id=6102")

Thank you, Toz, the solution from your link, being "xfwm4 is not restored by the session manager - you can either start xfwm4 with Alt+f2 or clear the session cache (rm -r ~/.cache/sessions)", does solve the problem.

---

### Post by graysky on 2011-10-19
Found this a google search for "xfce4 no window bars" and wanted to say thanks!  Same problem on my laptop.  Clearing the session and manually running xfwm4 once did the trick!

---

### Post by Budchekov on 2011-11-06
> **Copper Bezel said:**
> Try running xfwm4 --replace.

Many thanks Copper Bezel, this was the simple answer to a seemingly endless headache !:)

---

### Post by bkline on 2011-11-09
I, too, am very grateful for the workarounds.  I'd like to know what sorts of things could cause this problem, so I could perhaps avoid stumbling onto it in the future.  Thanks!

---

### Post by HousieMousie2 on 2011-11-14
> **Toz said:**
> From one of the xfce developers: [http://forum.xfce.org/viewtopic.php?id=6102]("http://forum.xfce.org/viewtopic.php?id=6102")

Thanks Toz!  Worked like a charm!

---

### Post by SnickerSnack on 2011-12-19
I had this problem too.  Honestly, I'm not sure how anyone is supposed to run commands when the problem is that you can't give focus to windows so that you can type in them. :confused:

Lucky for me (and maybe this is intended, but not said?) I use chromium, which is handled differently (not by the wm?) by default.  I was able to use google to find this page and then copy/paste the command into the run dialog.

How are others using this?

---

### Post by shebaw on 2011-12-25
> **Toz said:**
> From one of the xfce developers: [http://forum.xfce.org/viewtopic.php?id=6102](http://forum.xfce.org/viewtopic.php?id=6102)

Thank you Toz!

---

### Post by Pokey_blue32 on 2012-01-02
I have had this happen now on LXDE AND GNOME...most annoying when it happens on GNOME. It unloads somehow and refuses to reload on start.

GNOME..I thought the OS was broken as it happened so randomly..now LDXE did it. It UNLOADED on me!
What I dont understand is HOW this happened..

FPC starts acting up(as apparent when QEMU chokes on my compiled OS...I have to FORCE a reboot from another GeTTY, as the WM refuses to do it...now this...

Hard enough to get LinuxMint or Ubuntu(let alone Debian) configured and responsive...now this?
PISSED off enough about all the incomplete WM changes lately(mostly GNOME3)....

...and WINDOWS does not make my life easier as I work with OPEN SOURCE...

---

### Post by cybergalvez on 2012-02-09
> **koen.lefever said:**
> Thank you, Toz, the solution from your link, being "xfwm4 is not restored by the session manager - you can either start xfwm4 with Alt+f2 or clear the session cache (rm -r ~/.cache/sessions)", does solve the problem.

Thank you, I just had this problem and this fixed it for me

---

### Post by bkline on 2012-02-09
Anyone ever find out what's causing the problem in the first place?

---

### Post by obaino on 2012-05-03
I also experienced the same problem in Xubuntu 12.04.
xfwm4 --replace did the trick for me... but I am also interesting in finding out what causes the problem...

---

### Post by Toz on 2012-05-03
xfwm4 is crashing - you might be able to get some more info from ~/.xsession-errors, but you'd have to debug the process to try to get a better understanding. More information on debugging xfce & xfwm can be found here: [http://spurint.org/projects/xfce4-debugging/]("http://spurint.org/projects/xfce4-debugging/"). Most xfwm crashes tend to be random and not generated on demand, so it might be difficult to debug. However, if you do go through the debug steps, be sure to create a bug report [here]("https://bugzilla.xfce.org/") or [here]("https://bugs.launchpad.net/").

I remember reading somewhere that the developers were looking at adding in some code that would automatically restart it if it crashed, but can't find the reference. Not sure if its made it into the new 4.10 release. Unfortunately (or fortunately for me), xfwm doesn't crash on my computer so I can't debug it myself.

---

### Post by spamhier on 2012-05-08
> **Toz said:**
> From one of the xfce developers: [http://forum.xfce.org/viewtopic.php?id=6102]("http://forum.xfce.org/viewtopic.php?id=6102")

Thank you Toz. The problem still exists in xubuntu 12.04, but your solution also still works.

Regards,
SPamhier

---

### Post by Toz on 2012-05-08
> **spamhier said:**
> Thank you Toz. The problem still exists in xubuntu 12.04, but your solution also still works.

Regards,
SPamhier

I'm glad it worked for you. 

And welcome to the forums. Enjoy your stay.

---

### Post by NTL2009 on 2012-06-09
I'll add my THANKS!!!

I had been configuring my new Xubuntu 12.04 install, tweaking things and making great progress (BTW, I really like Xubuntu 12.04), when all the sudden it rebooted, and when it came back it was like I had told it to load the last session (I hadn't). Top menu bars of windows gone, the session managers for windows just blank. I had figured to re-install xfwm4, but I guess it was still not being told to run?

Well, I borked a few things in the process of trying to get it fixed until I found this, it worked a charm. Now to reset some things, and BACK IT UP!


Thanks again - NTL2009

---

### Post by bkline on 2012-08-12
Looks like lots of bug reports have been filed:
[LIST]
[*][NVIDIA disappearing title bar on Ubuntu 11.04]("https://bugs.launchpad.net/ubuntu/+source/icedtea-java7/+bug/791325")
[*][window title bar disappears completely on all windows]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/148958")
[*][window title bar missing]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/805665")
[*][Window title bar and borders disappear at random]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/683599")
[*][Title bars disappear and top panel is covered by menu bar]("https://bugs.launchpad.net/ubuntu/+bug/111659")[/LIST]

---

### Post by steveishere on 2012-09-22
This is a very helpful thread--thank you!  

I struggled with the same question someone previously had asked--how can you run xfwm4 when you can't even enter text into the box?  

I had the same problem, but when I rebooted my computer, I found I was able to hit Alt-F2 and this time, the system allowed me to enter the text into the box.  I find that with this bug, sometimes you can enter text and sometimes you can't and if you can't, rebooting helps.

---

### Post by bkline on 2012-09-22
I sure hope they fix this bug soon.  My wife was a happy Linux user until this problem struck, and she finally bailed into the Mac world after the problem got to be an almost daily occurrence, with no evidence that the developers were really interested in solving it. :-(

I may follow her (not for my servers of course) if this keeps up.

---

### Post by taj on 2012-09-24
Had the same problem here. The fix above worked. Thanks!
I agree with bkline that I hope that this will be fixed soon.

Edit: bug report: [https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/1055424](https://bugs.launchpad.net/ubuntu/+source/xfwm4/+bug/1055424)

<rant mode> To be honest: sofar Xubuntu Precise was not a pleasant experience. I upgraded from 100% working Ubuntu Lucid, Unity-2d froze a few times and I found 5 bugs that cost me a lot of time to work around. I cannot recommend this to new users, because one cannot run a system without the help of troubleshooting websites like this forum.</rant mode>

---

### Post by Toz on 2012-09-24
> **taj said:**
> 
<rant mode> To be honest: sofar Xubuntu Precise was not a pleasant experience. I upgraded from 100% working Ubuntu Lucid, Unity-2d froze a few times and I found 5 bugs that cost me a lot of time to work around. I cannot recommend this to new users, because one cannot run a system without the help of troubleshooting websites like this forum.</rant mode>

Xubuntu does not come with unity-2d, Ubuntu does. Xubuntu comes with Xfce.

I'm not saying that Xubuntu doesn't have issues of its own, but I think that your rant about unity-2d may be misplaced when talking about Xubuntu.

On a personal note, I have upgraded Xubuntu a number of times and have never had a problem. 

And on a plus side, having a friendly, knowledgeable forum like this to help people sort out issues is definitely a bonus in my eyes.

---

### Post by rai4shu2 on 2012-09-25
> **bkline said:**
> I sure hope they fix this bug soon.  My wife was a happy Linux user until this problem struck, and she finally bailed into the Mac world after the problem got to be an almost daily occurrence, with no evidence that the developers were really interested in solving it. :-(

I may follow her (not for my servers of course) if this keeps up.

You can't solve a problem that you can't reproduce. So, far I've looked through all these "bug reports" and can't help but notice how (when you actually find someone who produces a stack trace or something equally helpful) the problem is always related to a bad driver, to compiz, to Pango, or an upgrade gone bad. I highly doubt Mac or Windows would produce more satisfying results with similar treatment.

---

### Post by bkline on 2012-09-25
> **rai4shu2 said:**
> You can't solve a problem that you can't reproduce. So, far I've looked through all these "bug reports" and can't help but notice how (when you actually find someone who produces a stack trace or something equally helpful) the problem is always related to a bad driver, to compiz, to Pango, or an upgrade gone bad. I highly doubt Mac or Windows would produce more satisfying results with similar treatment.

I'll assume you're not implying that it's end users who are treating Ubuntu badly by agreeing to Ubuntu's suggestion that they upgrade their distribution, or by installing packages from the Canonical repositories.

I do sympathize with the developers who have to cope with the increasingly chaotic environment which Ubuntu has become.  The distro seems to have fallen into the trap Microsoft fell into, focusing more on introducing fancy new toys, than on making sure the pieces which are already in place are stable and play well together.

One thing that I think might help would be if there were troubleshooting tools more obviously accessible to the end user for collecting diagnostic information for tracking down the causes of failures.

---

### Post by rai4shu2 on 2012-09-25
> **bkline said:**
> I'll assume you're not implying that it's end users who are treating Ubuntu badly by agreeing to Ubuntu's suggestion that they upgrade their distribution, or by installing packages from the Canonical repositories.

...

One thing that I think might help would be if there were troubleshooting tools more obviously accessible to the end user for collecting diagnostic information for tracking down the causes of failures.

Actually, that's exactly what I was stating very plainly. Ubuntu is based on Debian Sid, which is notorious for breaking your upgrades. Why Ubuntu even makes a broken system available in the first place, I'll never understand. If you want a relatively stable Ubuntu system, you MUST install from scratch. Period.

The tools for debugging are already there, but I admit that it's a little starry-eyed of me to expect anyone but a dev to use them.

---

### Post by bkline on 2012-09-25
> **rai4shu2 said:**
> The tools for debugging are already there, but I admit that it's a little starry-eyed of me to expect anyone but a dev to use them.

That's sort of what I was getting at when I wrote "... more obviously accessible to the end user ...."

Can you tell me where to look for the logs which would provide clues as to the cause of this problem?

---

### Post by rai4shu2 on 2012-09-25
I've never had to troubleshoot xfwm, but I suppose you might get some clues from ~/.xsession-errors or maybe one of the recent /var/log files. That's where I would look, anyway.

---

### Post by taj on 2012-09-25
> **Toz said:**
> Xubuntu does not come with unity-2d, Ubuntu does. Xubuntu comes with Xfce.

I'm not saying that Xubuntu doesn't have issues of its own, but I think that your rant about unity-2d may be misplaced when talking about Xubuntu.

On a personal note, I have upgraded Xubuntu a number of times and have never had a problem. 

And on a plus side, having a friendly, knowledgeable forum like this to help people sort out issues is definitely a bonus in my eyes.

Sorry for not being clear. I upgraded from Ubuntu 10.04 to 12.04, i.e. from gnome to Unity. I had serious issues with Unity-2d (3d does not work on my hardware) so I was sort of forced to move to Xubuntu 12.04. As you saw in my I post I still have -albeit different- problems, and not everything is Window Manager related. My comments were about Ubuntu *and* Xubuntu 12.04. I do appreciate the hard work, but my work is held up by these bugs, more than in any earlier upgrade. Mind you, I use Ubuntu since Breezy, so I have some reason to be surprised.

---

### Post by bkline on 2012-09-25
> **rai4shu2 said:**
> I've never had to troubleshoot xfwm, but I suppose you might get some clues from ~/.xsession-errors or maybe one of the recent /var/log files. That's where I would look, anyway.

Thanks!

---

### Post by hofl on 2013-01-29
Wow, this thread was great and solved my problem in XUbuntu 12.04 LTS. I removed "~/.cache/sessions" recursive and restarted the PC. GREAT! THANK YOU!

---

### Post by bkline on 2013-01-29
Glad it worked for you.  Unfortunately, it doesn't look like the original problem is ever going to be fixed, and my wife (on whose machine this problem kept popping up more and more frequently) finally gave up.  She's a Mac user now.

---

### Post by llanitedave on 2013-02-08
I just discovered this thread, and it fixed my problem.  Removing "~/.cache/sessions" did NOT work, but xfwm --replace did.

This is the first major issue I've had with Xubuntu 12.10 and it was a little disconcerting.  I wouldn't run back to the Mac, though.  So far, my Kubuntu 12.10 has worked flawlessly.

---

