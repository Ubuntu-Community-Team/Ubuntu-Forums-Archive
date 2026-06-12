---
title: "Gnome Classic borders are missing"
date: 2011-07-04
forum: Desktop Environments
---

### Post by 73ckn797 on 2011-07-04
I am using 11.04. The Unity and Ubuntu Classic (no effects) are working as designed. The Ubuntu Classic DE has no window borders. I have searched and tried several solutions for similar issues but those have not worked. More info can be provided as requested.

This problem began after installing Lubuntu as an alternative DE and I have since removed it but the problem remains. I could have, in the time that I have been searching, re-installed Ubuntu but wanted to resolve this problem. The OS is on my laptop and I do not have any data that would be lost. The system has been setup with a separate /home partition so necessary/needed data will not be lost.

---

### Post by Krytarik on 2011-07-05
Check the setting "CompizConfig Settings Manager -> Window Decoration -> Command", it should be "/usr/bin/compiz-decorator".

Also make sure that those plugin is enabled.

Greetings.

---

### Post by 73ckn797 on 2011-07-05
> **Krytarik said:**
> Check the setting "CompizConfig Settings Manager -> Window Decoration -> Command", it should be "/usr/bin/compiz-decorator".

Also make sure that those plugin is enabled.

Greetings.
Everything is set as recommended already.

Here is output from several commands I have tried (commands in bold text):
```
computer@computer-Laptop:~$ **gconftool-2 --recursive-unset /apps/compiz-1**
```
No return on the first command

```
computer@computer-Laptop:~$ **unity --reset**
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done
** (<unknown>:2456): DEBUG: Unity accessibility initialization
** (<unknown>:2456): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1280x800

unity-panel-service: no process found
** (<unknown>:2456): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
** (<unknown>:2456): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:2456): DEBUG: PlaceEntry: Applications
** (<unknown>:2456): DEBUG: PlaceEntry: Commands
** (<unknown>:2456): DEBUG: PlaceEntry: Files & Folders
Starting unity-window-decorator
** (<unknown>:2456): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:2456): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:2456): DEBUG: Setting to primary screen rect: x=0 y=0 w=1280 h=800
** (<unknown>:2456): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus


(<unknown>:2456): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:2456): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:2456): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:2456): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:2456): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window

(<unknown>:2456): Gdk-WARNING **: /build/buildd/gtk+2.0-2.24.4/gdk/x11/gdkdrawable-x11.c:942 drawable is not a native X11 window
** (<unknown>:2456): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:2456): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:2456): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:2456): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:2456): DEBUG: IndicatorAdded: libme.so
** (<unknown>:2456): DEBUG: IndicatorAdded: libsession.so
** (<unknown>:2456): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:2456): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:2456): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:2456): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
```

---

### Post by Krytarik on 2011-07-05
I'm wondering why you are tinkering with "unity --reset" if it only concerns classic Gnome!?

Try running "gtk-window-decorator --replace" through the Alt+F2 dialog. Do the window decorations come up then?

---

### Post by 73ckn797 on 2011-07-05
> **Krytarik said:**
> I'm wondering why you are tinkering with "unity --reset" if it only concerns classic Gnome!?

Try running "gtk-window-decorator --replace" through the Alt+F2 dialog. Do the window decorations come up then?
That command is one that I already tried and it did not help.
The Alt+F2 dialog does not work in Ubuntu Classic DE. I can enter "metacity --replace" and the borders return but terminal does not return to the command line. When I close terminal the borders disappear.

---

### Post by Krytarik on 2011-07-05
> **73ckn797 said:**
> That command is one that I already tried and it did not help.
Make sure the packages "compiz" and "compiz-gnome" are installed.
> **73ckn797 said:**
> 
The Alt+F2 dialog does not work in Ubuntu Classic DE.
Make sure the plugin "Gnome Compatibility" is enabled in CCSM, and "Run Dialog" set correctly.

---

### Post by 73ckn797 on 2011-07-05
> **Krytarik said:**
> Make sure the packages "compiz" and "compiz-gnome" are installed.

Make sure the plugin "Gnome Compatibility" is enabled in CCSM, and "Run Dialog" set correctly.
All of that is set correctly. I looked into all of those options. It is only when using Ubuntu Classic DE. That is what has me stumped. I have also re-installed compiz and all related compiz packages.

---

### Post by Krytarik on 2011-07-05
Regarding the Run Dialog, is Gnome Panel running, as that is a feature of it?

Also, check if the key combination is set correctly in "Preferences -> Keyboard Shortcuts -> Show the panel's "Run Application" dialog box".

Regarding the core issue, please check if it's the same with another/new user.

---

### Post by 73ckn797 on 2011-07-05
I ended up reverting back to 10.04 via a fresh install. Upon restarting I  had the same problem. I then deleted all folders in /home that were not  application specific then re-installed 10.04. The problem no longer  exists. There must have been a config file in /home that was messed up  but I do not know what that was. I prefer the old Gnome DE anyway. I  will likely keep 10.04 LTS until the next LTS and decide whether I want  to stay with Ubuntu or use a different DE. I have been looking at  Lubuntu.

Thanks for the assistance.

---

### Post by Krytarik on 2011-07-05
> **73ckn797 said:**
> I  will likely keep 10.04 LTS until the next LTS and decide whether I want  to stay with Ubuntu or use a different DE.
Yeah, me too. ;-) But as I'm using AWN, there won't be an issue with Gnome3 anyway, whether or not Unity is on top, or whatever session options will be offered at that time.

---

### Post by moshuptrail on 2011-07-08
I solved by using CompizConfig Setting Manager > Effects > Window Decoration.  Enable it.  Then close and re-open any applications.  (Using Classic with Panel enabled)  I forget how I got the panel back.

---

### Post by 73ckn797 on 2011-07-08
> **moshuptrail said:**
> I solved by using CompizConfig Setting Manager > Effects > Window Decoration.  Enable it.  Then close and re-open any applications.  (Using Classic with Panel enabled)  I forget how I got the panel back.
This did not work. The panels were not the issue, only the window borders.

---

### Post by MG&amp;TL on 2011-07-11
Hello, OP. I have absolutely no idea why, but the output from unity --reset is the exact same as yours, therefore I got referenced by wildmanne39, to this thread. However, I'm having more of  a problem getting unity to appear in the first place, not issues with borders...hmmm...I'm sure wildmanne knows best.

My thread's here: (although it is enormous by now)

[http://ubuntuforums.org/showthread.php?t=1795383]("http://ubuntuforums.org/showthread.php?t=1795383")

---

### Post by gwi on 2011-09-29
> **73ckn797 said:**
> ... There must have been a config file in /home that was messed up  but I do not know what that was. ...
That's a pity, because I am facing the same problem. So far without a solution.

---

### Post by 73ckn797 on 2011-09-30
> **gwi said:**
> That's a pity, because I am facing the same problem. So far without a solution.
I feel the problem was in a /home folder. I am not going to install 11.04 again so the issue, for me, is over. 10.04 works fine so I do not need the latest version.

---

### Post by gwi on 2011-10-03
My problem is solved! See topic [Missing window decorations with Metacity and with Compiz]("http://ubuntuforums.org/showthread.php?t=1853088").
After removing the following files:
```
.local/share/applications/compiz.desktop
.local/share/applications/gnome-wm.desktop
.local/share/applications/metacity.desktop
```
the problem was gone.

---

