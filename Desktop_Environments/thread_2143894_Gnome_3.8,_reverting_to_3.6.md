---
title: "Gnome 3.8, reverting to 3.6"
date: 2013-05-10
forum: Desktop Environments
---

### Post by Derelinquat fenestras on 2013-05-10
Hello,
I'm running Ubuntu 13.04 on an Acer AspireOne notebook and recently installed Gnome 3.8 from 3.6, and there are several issues.  Prior to the upgrade, I was running Gnome fallback which was very stable, and now when I try to run it, I can no longer see the top and bottom panels.  When I run Gnome or Gnome Classic, they seem to run fine, but the background image is not displayed and only appears as a white screen with my desktop icons and I've tried adjusting the settings via the tweak tool to no avail...
I also can not seem to get the entire desktop to appear on my 10.5" screen... the bottom tray is 1/2 cut off and there are many instances where windows are cut off at the bottom, which frequently incapacitates the action of the window by cutting off the "cancel, Okay, etc" buttons.
I'm wondering either how to fix this issue or how to revert back to 3.6.

Any help would be greatly appreciated.  I have been using Ubuntu since 2007 and am fairly competent with the terminal and will fully comply with any further details required.

Thank you...

---

### Post by grahammechanical on 2013-05-10
You might find this thread useful

[http://ubuntuforums.org/showthread.php?t=2136093](http://ubuntuforums.org/showthread.php?t=2136093)

Are you sure that the issue is with Gnome 3.8 and not a video driver issue. I would advise using Synaptic Package Manager (not installed by default) as you can search for Gnome and identify which packages to remove and which to install as replacements. I would want to install Gnome 3.6 immediately after removing Gnome 3.8 otherwise you may lose the desktop completely.

Regards.

---

### Post by Derelinquat fenestras on 2013-05-10
Thank you for the reply.

I am attempting:
sudo ppa-purge ppa:gnome3-team/gnome3

to try to revert to Gnome 3.6

---

### Post by Frogs Hair on 2013-05-10
I removed 3.8 with synaptic on final beta and it was a complicated and long process . If you can locate and install the correct ppa purge/s start there or attempt to fix the problem . Classic in 3.8 is provided by an extension in the the Gnome Shell and not a separate session AFAIK.

---

### Post by Derelinquat fenestras on 2013-05-10
Thank you all for your responses!  
I was successful in reverting to Gnome 3.6.  
I opened a terminal and used the command:
[COLOR=#000000]sudo ppa-purge ppa:gnome3-team/gnome 
[/COLOR]It removed 3.8 and reinstalled 3.6, system works perfectly again.

Don't mean to sound ignorant to those who know better ways, but thank you aptitude!

For those who may not know, I believe I had to get ppa-purge from synaptic package manager.  It is also in the software center if you search ppa-purge.

---

### Post by engineerarun on 2013-10-20
This post might be of help for systems too messed up:
[http://oldpapyrus.wordpress.com/2013/10/20/rescue-ubuntu-from-unstable-ppa-issues/](http://oldpapyrus.wordpress.com/2013/10/20/rescue-ubuntu-from-unstable-ppa-issues/)

---

