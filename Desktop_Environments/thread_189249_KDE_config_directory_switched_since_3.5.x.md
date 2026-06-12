---
title: "KDE config directory switched since 3.5.x?"
date: 2006-06-05
forum: Desktop Environments
---

### Post by ThinkingFish on 2006-06-05
Yes, I'm using root, don't blame me for that because I am doing a lot of debugging work recently.
Then I notice my icon/wallpaper/decoration settings never take effect after setting them in the control panel, however, if I right click on window menu and make some change there, everything's just fine.

This drove me to dig a little deeper into the configuration files, this is what I found:
My old config files are all in /root/.kde/share/config/, while new ones reside in /root/share/config/. Sure about that because I compared the date and version info.  The old directory still displays kde version 3.4.3, while the new one 3.5.2. Also the kde-config -path shows current directory is the new one.

Maybe this explains my trouble, I think the settings in control panel still writes into the old file, while changing window property operates on new config files.](*,) 

What should I do now? How can I make all apps write to the same setting files?

---

### Post by ThinkingFish on 2006-06-05
I figured it out finally. Simply add 2 lines 

KDEHOME=$HOME/.kde
export KDEHOME

in /etc/bash.bashrc, or

KDEROOTHOME=$HOME/.kde
export KDEROOTHOME

/root/.bashrc, that solves the problem. But I still don't know how the ambiguity happened during upgrade :(

---

### Post by dreadnought1906 on 2006-06-05
Thanks very much indeed, that worked for me too.

---

