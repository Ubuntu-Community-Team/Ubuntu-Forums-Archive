---
title: "KDE Fonts problem"
date: 2005-12-06
forum: General Help
---

### Post by govedarov on 2005-12-06
Well I simply dont get it , I have installed the microsoft fonts and did some other things but my Firefox still looks so ugly :(( Can anyone tell me how to make it look good in a step by step way as it was written for Gnome ?

---

### Post by GoldBuggie on 2005-12-06
What you want is your GTK programs to look nicer. Do a ```
sudo apt-get install gtk2-engines-gtk-qt
``` Then go to *kcontrol -> Appearence & Themes -> GTK styles and fonts*. There you can set the font for your GTK apps. I have Use my *KDE fonts in GTK applications*. Restart firefox and enjoy. :D

If you feel that some gtk apps have ugly themes then you can change the theme at the same place. By default there aren't many themes installed in kubuntu for this(which is understandable). But you can install several. To show which are available do a ```
apt-cache search gtk2-engines
```. Then use apt-get to install the theme engine you want for your gtk apps.

---

### Post by govedarov on 2005-12-06
oh , I dont mean the programs look ugly , its not about the skins . I mean the text fonts what I am supposed to read when using browser is horrible :(((

---

### Post by GoldBuggie on 2005-12-06
oh..so if you want to install some regular used fonts the do a
```
sudo apt-get install msttcorefonts
```

or hmm...you did that already?!?!?

Then I'm not sure exactly what the problem is. Maybe changing your dpi? But then again if it is only firefox. hmmmm....sorry I'm at a loss at the moment

---

### Post by govedarov on 2005-12-07
I installed that already , but so what ....

---

### Post by oobuntoo on 2005-12-07
[QUOTE=govedarov]I installed that already , but so what ....[/QUOTE]


Yes, fonts rendering under linux is an annoying problem for new users, particularly when it come to web browsers. If you want something that look similar to what you see under Windows, some tweakings are needed. Here is  one way to do it:

First you need ms core fonts, which you may already have. If not install "msttcorefonts" package.
Then you need to tweak fontconfig by running the following command:
sudo dpkg-reconfigure fontconfig

Follow the onscreen instructions and try out various combinations until you find what you like. The combination that works really well for me is:
autohinter, never use subpixel rendering, and "no" to bitmap fonts.

Then, in your KDE System Settings or Kcontrol, under appearance/fonts, click on "configure" and choose "full" for hinting style. You may need to restart X by pressing Ctrl-Alt-Backspace.

Then, under Firefox fonts preferences, use Serif size 16 for proportional, Arial for Serif, Times New Roman for San-serif, Courier New size 12 for Monospace, 96 dpi for Display resolution.

You may need to add to xorg.conf file the "DisplaySize" along with correct values that correspond to your desktop screen size resolution. This will help program like Firefox displays fonts size correctly. Read the linked thread on how to do this:
[http://www.ubuntuforums.org/showthread.php?t=20976&highlight=cleartype]("http://www.ubuntuforums.org/showthread.php?t=20976&highlight=cleartype")

---

### Post by infoseeker on 2005-12-10
For KDE plus Gnome users please read this post:

[http://www.ubuntuforums.org/showthread.php?t=101559](http://www.ubuntuforums.org/showthread.php?t=101559)

---

