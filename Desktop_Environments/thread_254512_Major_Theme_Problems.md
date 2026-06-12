---
title: "Major Theme Problems"
date: 2006-09-10
forum: Desktop Environments
---

### Post by mocha on 2006-09-10
I can't figure this one out.  I initially installed Kubuntu, but then decided to try out the guide on Psychocats site for installing Gnome and keeping KDE as well.

For some reason when I'm in Gnome and if I go to Themes and attempt to change the theme to anything but "Human", things start to freak out.  Applets in the toolbar such as the clock and the volume control start to crash, and all the colors on the toolbar and icons go wierd.

Anyone seen this before?  Does it have anything to do with installing Gnome after Kubuntu?  I'm stuck with Human for now unless anyone has any suggestions.  Thanks.

---

### Post by lukew on 2006-09-10
I would create yourself a new user, see if this fixes the problem. Sounds like your themese are a bit messed.

Luke

---

### Post by llamakc on 2006-09-10
KDE's preferences for "Appearance (not sure what they call it)" has a checkbox for something akin to "use my QT style for GTK apps"--or something similar to that. I do not have the wording correct: I know. Just make sure that you haven't checked that and  haven't declared a GTK theme to use while USING KDE. That choice is also right in the same dialog box I'm poorly describing.

---

### Post by mocha on 2006-09-10
Thanks I'll try these suggestions.  What does the Appearance settings in KDE have to do with this problem though?  Are you saying that it affects Gnome?   I'm having the problem in Gnome, KDE seems to be unaffected.

---

### Post by chavo on 2006-09-11
I answered this one in this thread [http://ubuntuforums.org/showthread.php?t=187365](http://ubuntuforums.org/showthread.php?t=187365).

Like I said I came up with a fix for it, but I'm going to have to reopen the bug or file a new one. Read my post to understand how this affects your gnome login.

---

### Post by mocha on 2006-09-16
Thanks for your replys.  I ended up uninstalling ubuntu-desktop and now all is stable again.

---

### Post by Leonivek on 2006-09-21
> **llamakc said:**
> KDE's preferences for "Appearance (not sure what they call it)" has a checkbox for something akin to "use my QT style for GTK apps"--or something similar to that. I do not have the wording correct: I know. Just make sure that you haven't checked that and  haven't declared a GTK theme to use while USING KDE. That choice is also right in the same dialog box I'm poorly describing.

Hey, thanks! :p This helped solved [my similar problem]("http://linuxfud.wordpress.com/2006/09/20/ubuntu-panel-menu-bar-applet-loses-transparency-kde-affects-gnome/").  I initially installed Ubuntu, then decided to install the KDE environment.  At one point, I was playing around with the look of my desktop in Gnome and my Panel's menu bar and notification area handle wouldn't go transparent. :(  The rest of the panel did, but not those two. :confused:  Disabling that checkbox in KDE fixed that problem. \\:D/

Thanks, again!

---

