---
title: "Gnome panel applets crashing (OAFIID)"
date: 2008-05-28
forum: Desktop Environments
---

### Post by tamias on 2008-05-28
Hello all,

Since upgrading to Hardy my gnome-panel applets have been crashing on first startup with the error "Panel encountered a problem with loading OAFIID:GNOME_<applet>"

The applets in question are:

[LIST]
[*]ComputerTempApplet
[*]ComputerTempApplet
[*]MixerApplet
[*]StickyNotesApplet
[*]GWeatherApplet
[*]MultiloadApplet
[*]KeyboardApplet
[/LIST]

I am given the option to delete or keep them.

Not all my applets crash on startup (some load perfectly every time), and if I kill X with a Ctrl+Alt+BackSp then login again, all the applets restart with no problems.

I have tried all the proposed solutions I could find:

[LIST]
[*]Deleting pulse-$USER, orbit-$USER, gconf-$USER files from /tmp.
[*]aptitude reinstall gnome-applets gnome-applets-data (having issued /etc/init.d/gdm stop)
[*]Reinstalling each of the individual applets using aptitude.
[*]Removing python2.4 and aptitude reinstall-ing python2.5.
[*]Deleting the applets when queried and then manually adding and configuring them again.
[/LIST]

Despite all of these attempts, the same applets always crash on startup.

Anyone got any other ideas?

---

### Post by denham2010 on 2008-05-29
Hi,

Just a thought, can you check the startup order of the applets? (I am using XFCE so I am unsure of where you can find this with Gnome).

It sounds like the applets in question are trying to start before a certain service they require is started.

Try getting your applets to be the last items to start in your boot sequence and hopefully that will solve your issue.

I would post a link to a forum showing how to modify the startup order or programs, but the forum search is currently down.

Let us know how you get on!

---

### Post by tomcio on 2008-05-29
The same in my situation. Glipper crashes aways, when I start my system. I changes settings using gnome-session-properties, but it didn't help.

---

### Post by sween1911 on 2008-05-29
I got the "MixerApplet" problem, and it seemed to coincide with loss of my sound.

---

### Post by tamias on 2008-05-30
Thanks for your help so far!

> **denham2010 said:**
> Hi,

Just a thought, can you check the startup order of the applets? (I am using XFCE so I am unsure of where you can find this with Gnome).

It sounds like the applets in question are trying to start before a certain service they require is started.


I found what seems to be the configuration dialogue you mentioned at System -> Prefs -> Sessions -> Current Session.

> **denham2010 said:**
> Try getting your applets to be the last items to start in your boot sequence and hopefully that will solve your issue.


I also moved all the applets which I could locate in the list to a priority later than the default. (This included MixerApplet, StickyNotes, and ComputerTemp, but not GWeather, MultiLoad, or Keyboard.)

Unfortunately it turns out that this dialogue doesn't save the 'current session' options (which seems a bit strange as it has a 'startup order' spin box for each application, and an 'Apply' button!), so my applets priorities all reverted to the default 50 and crashed on startup again...

Edit: I tried it again, and this time the startup priorities were saved successfully. However the applets still crashed on login.

---

### Post by tamias on 2008-05-30
Update: I have located the relevant lines in my .xsession-errors file:
```

** (gnome-panel:6386): WARNING **: panel-applet-frame.c:1310: failed to get Bonobo/Control interface on applet OAFIID:GNOME_StickyNotesApplet:
Unknown CORBA exception id: 'IDL:omg.org/CORBA/COMM_FAILURE:1.0'
```

(and the same for KeyboardApplet, MixerApplet, MuliLoadApplet, GWeatherApplet, ComputertempApplet). Still no closer to finding a solution though...

---

### Post by tamias on 2008-05-31
Update again: the panel applets now seem to be loading correctly.

I've changed only one thing in my setup: I increased the panel size from 23 to 25 pixels. At 25 pixels, the panel appears the same physical height as at 23 pixels, which implies that the panel cannot be sized below 25 pixels, even if the preferences allow. I wonder if this was causing an error?

I'll try to confirm this later, and if decreasing the panel size causes the errors to reoccur I'll try to file a bug report, as this behaviour was not observed with Ubuntu 7.10.

---

### Post by gcastell on 2008-06-01
> **tomcio said:**
> The same in my situation. Glipper crashes aways, when I start my system. I changes settings using gnome-session-properties, but it didn't help.
I have the same problem with Glipper. changing the panel size didn't matter, I still have the problem.

---

### Post by gcastell on 2008-06-01
I found a solution for glipper [here]("https://bugs.launchpad.net/ubuntu/+source/glipper/+bug/213494").

---

### Post by belfasttim on 2008-06-02
I have the same issue, with MixerApplet, GNOME_Panel_TrashApplet and FastUserSwitchApplet.

---

### Post by tamias on 2008-06-02
Belfasttim, does increasing your panel size fix the issue?

Mark

---

### Post by belfasttim on 2008-06-02
> **tamias said:**
> Belfasttim, does increasing your panel size fix the issue?

Mark

Hi Mark-- how do I do this?

thanks

Tim

---

### Post by tamias on 2008-06-03
Right-click on your panel, go to Properties, and increase the size slowly until you see your panel start to grow, then reboot your computer (not just log out) to test if it works.

On my system, the original size was 23 pixels. By increasing this to 25, there was no visible change in the panel size, but the applets started loading correctly, which implies that the 'squeezing' of the applets in a panel which was too small was somehow leading to their crashing.

Above 25 pixels the panel begins to grow visibly, suggesting that 25 pixels is the minimum size that works, even if the panel properties will let you set it to < 25.

If this works for you, could you let me know your original panel size, and the new size that you set it to which made it work?

---

### Post by belfasttim on 2008-06-03
> **tamias said:**
> Right-click on your panel, go to Properties, and increase the size slowly until you see your panel start to grow, then reboot your computer (not just log out) to test if it works.

On my system, the original size was 23 pixels. By increasing this to 25, there was no visible change in the panel size, but the applets started loading correctly, which implies that the 'squeezing' of the applets in a panel which was too small was somehow leading to their crashing.

Above 25 pixels the panel begins to grow visibly, suggesting that 25 pixels is the minimum size that works, even if the panel properties will let you set it to < 25.

If this works for you, could you let me know your original panel size, and the new size that you set it to which made it work?


Hi Mark-- unfortunately, this didn't work for me. My panel was at 24 px, I set it at various widths from 25-30 px and same errors after reboot.

Thanks for taking the time to help though!

Tim

---

### Post by David Canarias on 2008-10-09
I am also having the same sort of problems and I am trying to find a solution. Yesterday I tried adding a new user and whne I clicked on F1 and put in the details up came a screen with lots of options I had to confirm. I touched one of the keys in this screen by mistake, couldn't find a way to correct it and had to accept. Well I now have the new user, but the OAFIID Applets are crashing. I don't know if this is relevant to anyone else or can help guide us. I will keep trying and thought I should let you know what happened in my case

---

### Post by suhtek on 2008-11-01
> **gcastell said:**
> I have the same problem with Glipper. changing the panel size didn't matter, I still have the problem.

this worked for me

 Originally Posted by mb_webguy  View Post
Glipper crashes because it tries to start before some of its dependencies, and it's an easy fix. Open a terminal and type "sudo gedit /usr/lib/glipper/glipper" and add the following two lines at the beginning of the file, after the comments:
Code:

#!/usr/bin/env python

# Glipper - Clipboardmanager for GNOME
# Copyright (C) 2007 Glipper Team
#
# blah, blah, blah...
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the
# Free Software Foundation, Inc., 59 Temple Place - Suite 330,
# Boston, MA 02111-1307, USA.
#

import time # <-- This line is new
time.sleep(8) # <-- This line is new.  Increase to 20 or 30 if 8 doesn't help

import gobject
gobject.threads_init()

And glipper has been maintained more recently than the gClip you linked to. Glipper was last updated in August of 2007, while gClip was last updated in January of 2007.

---

