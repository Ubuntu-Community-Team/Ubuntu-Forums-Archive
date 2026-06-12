---
title: "Themes showing in unity but not in cinnamon"
date: 2013-10-12
forum: Desktop Environments
---

### Post by AussiePozzie on 2013-10-12
Ubuntu 12.04 (3) x64
nvidia video
AMD CPU

After running scheduled update, cinnamon was also updated to 2.0.

Upon rebooting, cinnamon came back with crashing messages, refused to restart and reverted to gnome desktop.

Googling showed a missing file in the ppa, and changing the ppa to cinnamon-nightly, and running distribution upgrade, solved the problem of installation.

Further googling showed the need to upgrade nvidia from version 319 to version 325 (via edgers), which improved the display singnally.

Cinnamon is stable (so far), but is not displaying the themes, like icon, cursor, window and gtk themes at all, but is stuck steadfast on Adwiata.

gnome tweak tool and ubuntu tweak all show the selected themes in cinnamon, which display properly in unity and gnome only, but cinnamon displays only Adwiata.

Googling has produced not results so far.

Useful suggestions would be appreciated.:)

---

### Post by grahammechanical on 2013-10-12
Have you seen this?

[http://www.webupd8.org/2013/10/cinnamon-20-released-becomes-entire.html#more](http://www.webupd8.org/2013/10/cinnamon-20-released-becomes-entire.html#more)

> **Ubuntu 13.10, 13.04 or 12.10 (_there are some packages that [failed]("https://launchpad.net/~gwendal-lebihan-dev/+archive/cinnamon-stable/+packages") to build for Ubuntu 12.04 so I suggest you wait until these are fixed!_) users can install the latest stable Cinnamon by using the stable PPA.**

But you weren't given the choice.

Regards.

---

### Post by AussiePozzie on 2013-10-12
I did glance at this site before, should have maybe read it in a little more detail, but what I think, that this problem with some packages not building for 12.04, is rather easy to circumnavigate by reasigning the ppa to cinnamon-nightly, which then builts the packages correctly and installs them.

This isssue with the theme not changing I don't think is related to a build problem, rather to a structural problem inside the code.

I have meanwhile tried to get the theme changed via deconf-editor, but although is shows the correct selection, the theme still doesn't change.

If neither gnome tweak tool, nor ubuntu tweak nor deconf-editor manage to affect any change in the behaviour, than that would be a sound indication that some is amiss on the code level.

Thankx for you reply anyway.

---

### Post by Frogs Hair on 2013-10-12
Make sure you have Cinnamon 2.0 compatible themes. Cinnamon is its own desktop now not a shell running on gnome as the article states . The full Cinnamon desktop has it's own settings named Cinnamon Settings. I don't know if the Gnome Tweak tool is still applicable on the ppa version or not.

---

### Post by AussiePozzie on 2013-10-13
Googling for cinnamon compatible themes, I found that those are gkt3 themes, maybe I'm wrong. The ones I am trying cinnamon to display, are all gtk3 themes, like Zukitwo et. al.

I am aware of the cinnamon control center, but there are no settings for themes other then the ones for cinnamon directly, i.e. how to make the background colors of the menu change, what applets and other extensions to install etc. I have the cinnamon theme Adroit installed, it's working fine, equally so several applets, which work fine too.

There is no setting in cinnamon, or at least I couldn't find one, which allows me to change the icon theme or change the gtk3 theme.

If it were as you say, that cinnamon is now a complete desktop, then it raises the question why it is using Adwaita theme? Shouldn't it be that it would use it's **own** default theme, instead the default theme of gnome? I would think that the cinnamon programmers would be so professional and provide a specific cinnamon **default** theme if gnome themes were no longer useful to cinnamon.

Further, since dconf-editor is the overriding control unit for the **whole** of the system, then it follows that dconf should be able to override whatever settings there are in cinnamon, which it of course does, as I tried it, **save** the theme settings.

I do not claim any expertise in programming of PC programs, but when the highest control authority fails to make changes to a specific part of the system, than that is a sound indication of structural problems with the code, or that the programmers wish this setting to remain unchangeable, ...not likely in cinnamon.

---

### Post by Frogs Hair on 2013-10-13
I just installed the latest cinnamon ppa and was able to change my GTK theme, cinnamon shell theme, background, and icons  via settings . The GTK theme and icons were changed from settings> themes > other settings. The gnome tweak tool is not applicable to the cinnamon  installation . If you have tried this you may have a bug.

---

### Post by AussiePozzie on 2013-10-13
Thank you, **that did it!**

I think I need to gather sufficient courage to go and try out tabs and buttons that I **don't** know what they do!

Somthing that my mother tought me not to, ...

---

### Post by Frogs Hair on 2013-10-13
It usually does't hurt to look . ;)  Good luck with cinnamon !

---

