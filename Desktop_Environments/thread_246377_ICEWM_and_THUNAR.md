---
title: "ICEWM and THUNAR"
date: 2006-08-29
forum: Desktop Environments
---

### Post by ashrack on 2006-08-29
I find ROK-FILER very ackward and antiquated in ICEWM
So I installed THUNAR. BUt how do I make it the default FileManager and also when I lunch it there are no icons, heres the error when thunar is lunched from terminal:
```
(thunar:4975): Gtk-WARNING **: Could not find the icon 'gnome-mime-application-octet-stream'. The 'hicolor' theme
was not found either, perhaps you need to install it.
You can get a copy from:
        http://icon-theme.freedesktop.org/releases

```

---

### Post by ashrack on 2006-08-30
bump

---

### Post by BLTicklemonster on 2006-12-03
Better late than never...


```
# This is an example for IceWM's toolbar definition file.
#
# Place your variants in /etc/X11/icewm or in $HOME/.icewm
# since modifications to this file will be discarded when you
# (re)install icewm.
#
#prog XTerm xterm x-terminal-emulator
#prog FTE fte fte
#prog Netscape netscape netscape
#prog    "Vim" /usr/share/pixmaps/evolution-2.6.png evolution --component=mail
prog    "Nautilus" /noimageavailable.png nautilus --no-desktop
prog    "Thunar"   /noimageavailable.png thunar
prog    "Terminal" /usr/share/pixmaps/gnome-term.png gnome-terminal
prog    "Firefox" /home/bill/images/firefox.png firefox
prog     "UT" /home/bill/images/UT_category.png /home/bill/ut/ut
prog    "UTCacheCleaner" /home/bill/images/uttux.png /home/bill/utcleaner
prog    "WindowsXPPro" /home/bill/images/xp.png vmware
prog    "USP" /noimageavailable.png usp run-in-window
```

that's /home/you/.icewm/toolbar edited the way I use it.

---

### Post by kerry_s on 2006-12-03
> **ashrack said:**
> I find ROK-FILER very ackward and antiquated in ICEWM
So I installed THUNAR. BUt how do I make it the default FileManager and also when I lunch it there are no icons, heres the error when thunar is lunched from terminal:
```
(thunar:4975): Gtk-WARNING **: Could not find the icon 'gnome-mime-application-octet-stream'. The 'hicolor' theme
was not found either, perhaps you need to install it.
You can get a copy from:
        http://icon-theme.freedesktop.org/releases

```


What kind of setup are you running? The stock icons for thunar is "xfce4-icon-theme" & from the error you also need the "hicolor-icon-theme"

sudo apt-get install hicolor-icon-theme xfce4-icon-theme

Or use synaptic to install.

I haven't used icewm in a while so i can't remember if you have to set theme or they just get used. If you got gnome than you should be able to use usp, if not you can use a gtkrc-2.0 to set them.

---

### Post by BLTicklemonster on 2006-12-14
I guess I could have posted a bit of an easier post...

terminal:

thunar

press ctrl+h to show hidden folders

go to .icwm

open "startup" in text editor

add the line

thunar &

save, 

now open "toolbar"

and add this line

prog    "Thunar"   /noimageavailable.png thunar


restart icewm ( I guess) then log out and back in.

You will have thunar on your toolbar. 

(actually you can just add thunar to toolbar and not mess with that first stuff. if you have rox panel already in startup, leave it so you can have icons on your desktop, and just remove the home folder there)

---

### Post by vronp on 2007-02-07
Here is a nice thunar icon for the tool bar:

[http://svn.xfce.org/svn/xfce/thunar/trunk/icons/48x48/Thunar.png](http://svn.xfce.org/svn/xfce/thunar/trunk/icons/48x48/Thunar.png)

---

### Post by BLTicklemonster on 2007-02-07
Thanks for that awesome icon, vronp!

I looked back over this, and decided to clarify something in the toolbar post I did.


for each of these:

prog    "Thunar"   /noimageavailable.png thunar

"Thunar" is the name that will show up.

/noimageavailable.png is a link to the icon. Say you have thunar.png in /home/you/ then it would be /home/you/thunar.png of course.

then after that, it say

thunar

that is what you can put in terminal to launch thunar. Some programs need a path, which is why you will see the path on some of them, i.e.

prog    "UTCacheCleaner" /home/bill/images/uttux.png /home/bill/utcleaner

I reckon some people might look at the code and wonder what the heck, so there it is in plain simpleish.

---

