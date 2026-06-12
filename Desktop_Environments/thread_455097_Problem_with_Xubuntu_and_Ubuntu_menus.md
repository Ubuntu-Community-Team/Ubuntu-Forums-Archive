---
title: "Problem with Xubuntu and Ubuntu menus"
date: 2007-05-26
forum: Desktop Environments
---

### Post by samjh on 2007-05-26
I've just installed Xubuntu with "sudo aptitude xubuntu-desktop" and removed Ubuntu by using the commands on the Psychocat's Ubuntu Tutorials website.

Everything is working fine, except the application menu.

It shows this:
[IMG]http://img154.imageshack.us/img154/6042/untitled1lm6.png[/IMG]

Noticing that several of the entries were to files that no longer exist, I tried to remove it with the menu editor, but it only shows:
[IMG]http://img503.imageshack.us/img503/4821/untitleded2.png[/IMG]

Which leaves me perplexed as to where Xfce is reading those erroneous entries from.  It looks like my old menu items from Ubuntu have crossed into Xfce's menu, but some of those entries didn't even exist in my old Ubuntu menu (I know this because I manually deleted them a few days ago).

Could someone help me (and any future users who might come across a similar problem) to rid those obsolete entries from the menu?

---

### Post by bapoumba on 2007-05-27
Which applications do not exist any longer and have a menu entry ? (and I have the same exact menu-editor as shown on our screenshot).

---

### Post by aidanr on 2007-05-27
include system is the entries from your gnome installation, these are entries in /usr/share/applications and ~/.local/share/applications and can be edited with alacarte

xfce's menu entries are stored in ~/.config/xfce4/desktop

personally i just prefer to remove the system entry and recreate the menu items i use most

---

### Post by paxmark1 on 2007-06-05
Hi, clean install of xfce instead of an upgrade from 6.10 Kubuntu.  I had no menus for a bit, but got them enabled.  

However I cannot drag windows.  Also the little maximixe, ,minimize and kill buttons on the top right are not present.  

No web for a while, and no updates, but I do now, and still, I have missing aspects.  also, keyboard input for things goes whacko at times.  I have never seen anything like this previous.

TIA  

Mark

---

### Post by bapoumba on 2007-06-05
> **paxmark1 said:**
> Hi, clean install of xfce instead of an upgrade from 6.10 Kubuntu.  I had no menus for a bit, but got them enabled.  

However I cannot drag windows.  Also the little maximixe, ,minimize and kill buttons on the top right are not present.  

No web for a while, and no updates, but I do now, and still, I have missing aspects.  also, keyboard input for things goes whacko at times.  I have never seen anything like this previous.

TIA  

Mark
Hum. may be the theme ? Is this a laptop ?

---

### Post by paxmark1 on 2007-06-06
thanks.  

Not a laptop, small form factor with a 2.4 celeron.  

I have gone with Kubuntu since 5 something. Mandrake before and Caldera previous.   Kubuntu and .deb packaging works real well, but htop has been showing much more system overhead on KDE stuff as time goes by.  I had a LCD, but now have a 15 inch monitor.

I decided on a clean install for system and to go straight to Xfce.  However I still have my old . files in /home/~

Flaky for keyboard menu input, in Pysol and Opera and Mozila.  I thought Opera was not being opened, but discovered it was opening into a line about 3 inches top to bottom.  And at the upper right no buttons to min, max, or close.  I could not drap open windows or resize. Ssince I could not minimze via button, I had to close windows to start other apps.  Xfce terminal was at top and stopped 2/3rds way down.  konsole started halfway up and extended below screen.

sudo apt-get kubuntu-desktop  and everything is groovy in KDE desktop (except for the system load as diagnosed by htop).  Same wallpaper as 6.10 

Now suddenly Xfce is just the previous wallpaper picture and no menus or title bars or icons.  It comes via KDM.  

But hey, the new Hawking USB wlan with the antenna really works well, even though it was a bit of fiddling in files and make, make install of rt73 driver,   Real smooth download of KDE desktop.  Any ideas to get Xfce up appreciated, no hurry though.

TIA   mark

---

### Post by bapoumba on 2007-06-06
Do you have access to the xfce menu ?
Settings > Desktop settings > Tick allow xfce to manage the desktop.

---

