---
title: "Looking for IceWM Customization Tips"
date: 2007-09-17
forum: Desktop Environments
---

### Post by wersdaluv on 2007-09-17
I want[*]IceWM's default looks awful (at least for me). How does your desktop look like?[*]I want to have keyboard shortcuts for minimizing windows, making windows full screen, etc.; but IceWM does not seem to support shortcuts. Does it? If so, how do I set shortcuts, and what are your own shortcuts, aysiu?

 to use IceWM because it is so fast (I have a humble hardware) and aysiu seems to have the right reasons for using it, but it (vanilla IceWM) does not work for me.
[*]I do not like the way I hunt for apps in IceWM. The menus have to be pressed for submenus and the grouping of the programs is confusing. What did you do about that?

I want to know more about aysiu's IceWM laptop (if he really is running it on his laptop) because I believe that the defaults really needs some tweaking. 

Here is my list:


---

### Post by wersdaluv on 2007-09-17
I want to use IceWM because it is so fast (I have a humble hardware) and aysiu seems to have the right reasons for using it, but it (vanilla IceWM) does not work for me.

I want to know more about aysiu's IceWM laptop (if he really is running it on his laptop) because I believe that the defaults really needs some tweaking. 

Here is my list:
[LIST][*]IceWM's default looks awful (at least for me). How does your desktop look like?[*]I want to have keyboard shortcuts for minimizing windows, making windows full screen, etc.; but IceWM does not seem to support shortcuts. Does it? If so, how do I set shortcuts, and what are your own shortcuts, aysiu?[*]I do not like the way I hunt for apps in IceWM. The menus have to be pressed for submenus and the grouping of the programs is confusing. What did you do about that?
[/LIST]

I'll just add more to this list later...

---

### Post by aysiu on 2007-09-17
There are some good tips in [this thread](http://ubuntuforums.org/showthread.php?t=263710), and you can define a keyboard shortcut for just about anything.

Read the first three pages of the thread. That should be a good start.

The theme I use is called ThinBlack, and it's pretty spiffy-looking:
[http://ubuntuforums.org/showthread.php?t=321994](http://ubuntuforums.org/showthread.php?t=321994)

---

### Post by aysiu on 2007-09-17
> **wersdaluv said:**
> 
IceWM's default looks awful (at least for me). How does your desktop look like? I've attached a screenshot. I'm using ThinBlack for the IceWM theme, RedShift for the Firefox theme, and BlackJapan for the Thunderbird theme. > I want to have keyboard shortcuts for minimizing windows, making windows full screen, etc.; but IceWM does not seem to support shortcuts. Does it? As far as I know, IceWM supports shortcuts for all of those without even customizing the shortcuts. Control-Alt-D shows the desktop (minimizing all windows). Alt-Tab switches between windows. And I believe Alt-F10 maximizes windows. Another handy one is Windows-Space Bar, which gives you a quick run menu in the toolbar. > If so, how do I set shortcuts, and what are your own shortcuts, aysiu? You define keyboard shortcuts by creating a text file called ~/.icewm/keys. Here's what mine looks like: ```
# Valid modifiers are Alt, Ctrl, Shift, Meta, Super and Hyper.

# Super is the Windows key
# Ctrl is the Control key

key "Alt+F2" grun

#key "XF86Standby"		killall -QUIT icewm

key "Super+Up" aumix -v +3
key "Super+Down" aumix -v -4

key "F13"	aumix -v +4
key "F14"	aumix -v -4
key "F15"	aumix -v 0

key "Alt+Shift+g"	gksudo gdmsetup
key "Alt+Shift+h"	gksudo thunar

key "Alt+Print" gnome-screenshot --window
key "Print" gnome-screenshot
key "Ctrl+Shift+p" gnome-screenshot --delay 8

key "Super+a" galeon
key "Super+b" quodlibet --play-pause
key "Super+c" gcalctool
key "Super+d" dillo
key "Super+e" evolution 
key "Super+f" firefox
key "Super+g" gdmflexiserver --xnest
key "Super+h" thunar
key "Super+i" rhythmbox-client --next
key "Super+j" sound-juicer
key "Super+k" xkill
key "Super+l" leafpad
key "Super+m" aumix -v 0
key "Super+n" quodlibet --next
key "Super+o" rhythmbox-client --notify
key "Super+p" 
key "Super+q" quodlibet
key "Super+r" rhythmbox
key "Super+s" gksudo synaptic
key "Super+t" mozilla-thunderbird
key "Super+u" rhythmbox-client --play-pause
key "Super+v" quodlibet --previous
key "Super+w" oowriter
key "Super+x" xterm
key "Super+y" rhythmbox-client --previous
key "Super+z" filezilla

``` I believe you can also copy (and modify) one from /usr/share/icewm/keys. > I do not like the way I hunt for apps in IceWM. The menus have to be pressed for submenus and the grouping of the programs is confusing. What did you do about that? I don't remember. I may have manually configured the menu, or maybe I installed *menu-xdg*, which I think auto-populates the menu with your installed applications.

---

### Post by wersdaluv on 2007-09-18
Thanks aysiu!

By the way, I found this great [IceWM page]("http://yakubovich.blogspot.com/2006/11/use-icewm.html"). You may want to look at it too. :KS

---

