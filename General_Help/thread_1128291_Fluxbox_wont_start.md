---
title: "Fluxbox wont start"
date: 2009-04-17
forum: General Help
---

### Post by inxygnuu on 2009-04-17
Hello, i just got my fluxbox working the way i want  it, then just a while ago i restart my computer and it wont start. all of my startup programs load, but there is nnow windows decoration, and i am unable to right click on the desktop to start anything. The fluxbox bar does not start either. Does anyone know what is going on?:(

Any help would be appreciated,
3v4n

---

### Post by joshdudeha on 2009-04-17
Have you added it to the start-up programs? 
Is it replacing metacity?

---

### Post by inxygnuu on 2009-04-17
no. I am not launching it into gnome, I am launching it as a session. when i login, all of my startup programs open, but none have a windows decorator. they are unmovable windows.

---

### Post by uncle-c on 2009-04-17
Are you starting your desktop via a login manager like gdm or from command line ? If the latter then you may have to edit your .xinitrc file.

---

### Post by inxygnuu on 2009-04-17
i am booting it from a login manager. I believe i am using gdm.

---

### Post by Anzan on 2009-04-18
Perhaps check what's in your Startup file in .fluxbox.

---

### Post by inxygnuu on 2009-04-18
Fixed!:D:popcorn::KS

---

### Post by Anzan on 2009-04-18
Great.

---

### Post by inxygnuu on 2009-04-19
Is there still a way to mark threads as solved?

---

### Post by Flotter on 2009-04-30
> **inxygnuu said:**
> Fixed!:D:popcorn::KS

How'd you fix it, and what was wrong??

I'm having problems getting mine running again after upgrading to jaunty.  Here's the error messages I'm getting from my .xsession-errors file:

Xsession: X session started for jamstar7 at Mon Apr 20 14:00:41 MST 2009
/etc/X11/Xsession.d/40guidance-displayconfig_restore: line 11: /usr/bin/displayconfig-restore: No such file or directory
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open file '/usr/share/kubuntu-default-settings/kubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
wmnet: using devstats driver to monitor eth0
Failed to read: session.screen0.maxIgnoreIncrement
Setting default value
Failed to read: session.screen0.maxDisableMove
Setting default value
Failed to read: session.screen0.maxDisableResize
Setting default value
Failed to read: session.screen0.noFocusWhileTypingDelay
Setting default value
Failed to read: session.screen0.tooltipDelay
Setting default value
Failed to read: session.screen0.clientMenu.usePixmap
Setting default value
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 95 requests (48 known processed) with 0 events remaining.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 1458 requests (142 known processed) with 0 events remaining.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 288 requests (240 known processed) with 0 events remaining.
No protocol specified
bt::Display: failed to open display ''

---

