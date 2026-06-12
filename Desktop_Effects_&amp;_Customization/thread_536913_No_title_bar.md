---
title: "No title bar"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by strumica on 2007-08-28
HI, 
I am kinda new around here, installed ubuntu 7.04 and beryl manager right after as explained on [http://ubuntuforums.org/showthread.php?t=488385&highlight=beryl+ati+radeon](http://ubuntuforums.org/showthread.php?t=488385&highlight=beryl+ati+radeon). Everything's working but one thing: I don't have title bar on any window now :( anyone knows what to do?

Thanks

---

### Post by bobbybobington on 2007-08-28
Yeah, I get that sometimes. Try clicking on the beryl icon on the top panel (right or left click I can't remember) and click on reload window decorator. That usually does the trick.

---

### Post by mahiyar on 2007-08-28
You can do two things right click the beryl settings, select metacity from "select windows manager" now you should see the title bar, try switching back to beryl again. Or follow this link [http://linuxmint.com/forum/viewtopic.php?t=657](http://linuxmint.com/forum/viewtopic.php?t=657)

---

### Post by strumica on 2007-08-28
Tried everything you have suggested, but it just don't work, I have the title bar while using metacity as window manager, but when I switch back to beryl they go away. I have "something" like title bar while using compiz from the "select window manager" option, i have the title bar but i can not see it, I can drag the window, and I "have" the close, minimize and maximize buttons, but I don't see them, when I go with mouse over, I can see they are here. Am I making any sense?

---

### Post by strumica on 2007-08-28
By the way I am using Acer aspifre 5100 laptop, with athlon 64, ATI radeon 1100 integrated, have 1GB of RAM memory

---

### Post by andywang603 on 2007-08-28
> **strumica said:**
> Tried everything you have suggested, but it just don't work, I have the title bar while using metacity as window manager, but when I switch back to beryl they go away. I have "something" like title bar while using compiz from the "select window manager" option, i have the title bar but i can not see it, I can drag the window, and I "have" the close, minimize and maximize buttons, but I don't see them, when I go with mouse over, I can see they are here. Am I making any sense?

exactly same Issue I'm having, I'm using X61 thinkpad with x3100 videocard...

any one has sulution?

BTW, if I choose gtk window manager,then everything seems just fine, when I choose beryl as the wmanager, then the issue comes up

---

### Post by mahiyar on 2007-08-28
As a last resort try deleting the .beryl folder in your home directory and then restart beryl.

---

### Post by strumica on 2007-08-29
I tried even that, now I got black screen after starting beryl, and I can't see anything. Tried to restart it a few times, no changes. Now i choose a session of gnome only without XGL, because if I login in XGL i have black screen only. help!

---

### Post by augerb on 2007-08-29
If you have nvidia:

in a terminal type
sudo nvidia-xconfig --add-argb-glx-visuals

---

### Post by strumica on 2007-08-29
I am using Acer aspifre 5100 laptop, with athlon 64, ATI radeon 1100 integrated, have 1GB of RAM memory

---

### Post by sdowney717 on 2007-08-29
since beryl merged into compiz and is no longer being developed, why not just use compiz-fusion for desktop effects?
set up an XGL session because of your ATI card
use the emerald theme manager for window decoration

start compiz  by typing compiz --replace -c emerald

in compiz the plugin is called window decoration for the title bar

---

### Post by strumica on 2007-08-29
tried, this is what i got:

~$ compiz --replace -c emerald
core, ccp, dbus, place, move, resize, decoration, png, wobbly, cube, fade, minimize, rotate, scale, switcher, regex, workarounds, zoom, done
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

---

### Post by sdowney717 on 2007-08-29
if you have compiz-fusion installed try going into  the settings manager
under preferences set it to flat file backend
AND click the resets to default button

---

### Post by michael37 on 2007-08-29
> **strumica said:**
> tried, this is what i got:

~$ compiz --replace -c emerald
core, ccp, dbus, place, move, resize, decoration, png, wobbly, cube, fade, minimize, rotate, scale, switcher, regex, workarounds, zoom, done
(blah blah)
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


I believe you might have a problem with libdecorations which doesn't match your compiz.  Try a complete uninstall from [ this guide](http://ubuntuforums.org/showthread.php?t=533201).  Then, perform a clean reinstall from [this guide](https://help.ubuntu.com/community/CompositeManager/CompizFusion).

---

