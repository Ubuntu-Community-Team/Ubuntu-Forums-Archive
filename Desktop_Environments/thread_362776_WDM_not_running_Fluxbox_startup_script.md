---
title: "WDM not running Fluxbox startup script"
date: 2007-02-16
forum: Desktop Environments
---

### Post by ahobbs on 2007-02-16
I'm having a bit of an annoying problem with WDM and the Fluxbox startup script (located in ~/.fluxbox/startup) in Dapper that I can't seem to figure out.  I've been trying to run fbdesk (or any program, for that matter) at the startup of fluxbox without success.

It appears as though my ~/.fluxbox/startup script is not accessed after logging on via WDM.  The reason why I believe this is that I renamed the ~/.fluxbox/startup file to something else, and fluxbox appears to startup as usual.

After researching Fluxbox documentation, the fluxbox wdm wiki ([http://fluxbox-wiki.org/index.php/WDM](http://fluxbox-wiki.org/index.php/WDM)), and scouring the forum, I'm still as confused as ever.  If anyone has any ideas, I would greatly appreciate it!

---

### Post by kerry_s on 2007-02-16
Did you select fluxbox in the session menu? Why not just use gdm?

---

### Post by ahobbs on 2007-02-16
> **kerry_s said:**
> Did you select fluxbox in the session menu?

Yes, fluxbox is starting up fine, but the ~/.fluxbox/startup file is not being accessed for user preferences (I think).

> **kerry_s said:**
> Why not just use gdm?

Please explain advantages and disadvantages of gdm over wdm.  (BTW, I'm running a very minimal server install...)

---

### Post by yabbadabbadont on 2007-02-16
Assuming that WDM uses the same session file as GDM, what are the contents of /usr/share/xsessions/fluxbox.desktop?

---

### Post by ahobbs on 2007-02-16
> **yabbadabbadont said:**
> Assuming that WDM uses the same session file as GDM, what are the contents of /usr/share/xsessions/fluxbox.desktop?

My /usr/share/xsessions/fluxbox.desktop file looks like this:

> [Desktop Entry]
Encoding=UTF-8
Name=Fluxbox
Comment=Highly configurable and low resource X11 Window manager
Exec=/usr/bin/startfluxbox
Terminal=False
TryExec=/usr/bin/startfluxbox
Type=Application

[Window Manager]
SessionManaged=true

---

### Post by yabbadabbadont on 2007-02-16
That desktop file is correct an should run your ~/.fluxbox/startup file.  My guess is that WDM does not use that session file and is instead configured somewhere else.  Time to do some reading...  :D

I think I saw an article on configuring WDM session on the Gentoo Wiki, but I'll have to do some searching to be sure.

---

### Post by yabbadabbadont on 2007-02-16
OK, after reading the only docs I could find: [http://voins.program.ru/wdm/INSTALL](http://voins.program.ru/wdm/INSTALL)

It looks like you need to look through the files in /etc/wdm and modify any fluxbox related entries so that they call startfluxbox and not just fluxbox.  The startfluxbox script should always be used to startup fluxbox properly.  Any other method is prone to errors.

---

### Post by yabbadabbadont on 2007-02-16
[http://fluxbox-wiki.org/index.php/Howto_add_fluxbox_to_wdm](http://fluxbox-wiki.org/index.php/Howto_add_fluxbox_to_wdm)

Perhaps it is /etc/X11/wdm and not /etc/wdm.

---

### Post by ahobbs on 2007-02-17
> **yabbadabbadont said:**
> OK, after reading the only docs I could find: [http://voins.program.ru/wdm/INSTALL](http://voins.program.ru/wdm/INSTALL)

It looks like you need to look through the files in /etc/wdm and modify any fluxbox related entries so that they call startfluxbox and not just fluxbox.  The startfluxbox script should always be used to startup fluxbox properly.  Any other method is prone to errors.

I REALLY appreciate you looking into this for me, yabbadabbadont.  In my forums searches, I read many of your posts, and I think you're a saint for helping so many people with fluxbox.

Anyway, I don't have a /etc/wdm folder.  I do have a /etc/X11/wdm folder and the only occurance of 'fluxbox' occurs in /etc/X11/wdm/wdm-config on the following line:

> DisplayManager*wdmWm:         default:fluxbox

Does this line need to change to startfluxbox as you've indicated, or should we be looking somewhere else?

---

### Post by yabbadabbadont on 2007-02-17
I pretty sure you just need to change that:

DisplayManager*wdmWm: default:fluxbox

to be:

DisplayManager*wdmWm: default:startfluxbox

---

### Post by ahobbs on 2007-02-17
> **yabbadabbadont said:**
> I pretty sure you just need to change that:

DisplayManager*wdmWm: default:fluxbox

to be:

DisplayManager*wdmWm: default:startfluxbox

BINGO! :KS

Not only did I have to modify etc/X11/wdm/wdm-config as stated above, but I also had to modify /etc/X11/wdm/wdm.options and comment out the line "auto-update-wmlist", otherwise the DisplayManager*wdmWm default would be overwritten with fluxbox on every wdm restart.

Thank you yabbadabbadont!!!

---

### Post by kerry_s on 2007-02-17
I done hundreds of server installs, if want to use a log in manager GDM is the best. You won't get those problems your getting with those older login managers. The size is worth the less head aches.

Create a file in your home .xinitrc put->

exec /usr/bin/startfluxbox
or
exec /home/(you)/.fluxbox/startup

make sure your startup is executable.
That should make WDM work right.
Hey worked it out. To give you a idea of the age, the last update was 2005-> [http://voins.program.ru/wdm/index.html.en](http://voins.program.ru/wdm/index.html.en)

---

