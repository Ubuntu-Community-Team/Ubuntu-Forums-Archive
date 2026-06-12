---
title: "Panel slow to open and network flaky"
date: 2010-06-10
forum: Desktop Environments
---

### Post by reedk on 2010-06-10
Since a couple days ago, the top and bottom gnome panels take a long time (~25 secs) to appear. At the same time, Firefox now starts up in offline mode, and has to be put in online mode to work.
Based on some threads, I tried setting /etc/NetworkManager/nm-system-settings.conf from
```
[ifupdown]
managed=false
```
to
```
[ifupdown]
managed=true
```
But the problem persists.
I also thought it might be related to a gconf setting so I created a new test user but the test user also has a long time to wait for the panels.

Any thoughts or leads?

---

### Post by reedk on 2010-06-11
Update: The networking seems fine but the panel is slow to appear and slow to launch Evolution. What's odd is that *my* account does not have the problem - the panels show up right away - but every other user, including the new test user - does have the slow-to-appear panels.

---

### Post by wolferl on 2010-06-12
> **reedk said:**
> Update: The networking seems fine but the panel is slow to appear and slow to launch Evolution. What's odd is that *my* account does not have the problem - the panels show up right away - but every other user, including the new test user - does have the slow-to-appear panels.

Yes, I'm experiencing the same problem with the panel. We have 5 accounts on the PC and only one seems to load the panel normally, the rest take half a minute to load the panel.

This seems like a common bug and I guess it will go more common as more users update their systems......................

---

### Post by reedk on 2010-06-12
Another thread [**(Panel takes ages to load on login with Lucid)**]("http://ubuntuforums.org/showthread.php?t=1497083&highlight=panel+ages") talked about re-creating your existing panel and then deleting the original. I'll try that this afternoon and post the results. Evolution seems to take a long time to load as well; I can't tell if that related.

---

### Post by reedk on 2010-06-13
Try removing the date/time applet from your panel and trying again. This worked for me (at the cost of no longer having the date displayed). If that does it for you too I will file a bug.

---

### Post by simon_w on 2010-06-17
Argh - gnome-panel is sooo flaky!

frequently it takes ages, or doesn't start.  (I actually have a keyboard shortcut to restart the panel, it's that frequent a problem).

when it does start, i'm usually (yes, not *often*, but actually *usually*) missing an applet or two, most commonly the date/time applet.  also common is losing the indicator applet (and trashing ~/.gconf/apps/panel/applet_0/%gconf.xml - my indicator applet keys - so it won't come back)

sometimes when it starts, it tops out my processor and I have to restart it.

working on multiple monitors is a nightmare - the applets are in a different order every time I change my desktop resolution.

the upshot of all this is that I have to restart, log out/log in, restart gnome-panel anything up to half a dozen times until it's all working, every time I log in.  Frankly, it's embarrassing!

so far my best solution is to have a script (accessibly from a keyboard shortcut or a tiny GUI bound to a keyboard shortcut) which trashes the relevant gconf settings, rebuilds them from a correct backup, and then restarts the panel.  This has (approximately) a 50% success ratio, but it's an improvement.

It's worth noting that most of these problems have been with me one way or another since I began using Ubuntu and Gnome, with Feisty, (especially the applets shuffling around - gconf's 'panel_right_stick' flag just won't stay set) but they're clearly worse for me under Lucid.

sorry for the rant, but i feel a little better!  this frustrates me every single day.

I have a whole mess of crap in my $HOME/.xsession-errors - i'm posting some stuff that looks like it might be relevant.  if anyone else has similar problems, perhaps you could do the same, and maybe we can find some clues :)

```

I/O warning : failed to load external entity "/home/simon/.compiz/session/104bee8ad5fc5de0d1127682790415659500000037120037"
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

(polkit-gnome-authentication-agent-1:3838): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:3838): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:3823): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x1ae4320'
** Message: adding killswitch idx 0 state 1
** Message: killswitch 0 is 1
** Message: killswitches state 1
** (bluetooth-applet:3840): DEBUG: Unhandled UUID 00001120-0000-1000-8000-00805f9b34fb (0x1120)
** Message: killswitch 0 is 1
** Message: killswitches state 1


```

---

### Post by simon_w on 2010-06-17
ah - after wading through a little more, this seems to be more relevant:

```

(gnome-power-manager:2590): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nautilus:2589): GLib-GObject-WARNING **: invalid cast from `NautilusWindowPane' to `NautilusNavigationWindowPane'
X Error of failed request:  BadDamage (invalid Damage parameter)
  Major opcode of failed request:  158 (DAMAGE)
  Minor opcode of failed request:  3 (XDamageSubtract)
  Serial number of failed request:  35677
  Current serial number in output stream:  35678
** Message: Active session changed
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

(polkit-gnome-authentication-agent-1:2603): polkit-gnome-1-WARNING **: Error enumerating temporary authorizations: Remote Exception invoking org.freedesktop.PolicyKit1.Authority.EnumerateTemporaryAuthorizations() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.PolicyKit1.Error.Failed: Cannot determine session the caller is in

** (gnome-user-share:3186): WARNING **: Couldn't request the name: Unable to find session for cookie
gtk-redshift: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
parcellite: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
dropbox: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gtkdialog: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 227 requests (226 known processed) with 0 events remaining.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
The application 'gnome-panel' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.


** (gnome-panel:3145): WARNING **: panel-applet-frame.c:1273: failed to load applet OAFIID:GNOME_ClockApplet:
System exception: IDL:omg.org/CORBA/COMM_FAILURE:1.0

(scim-panel-gtk:3665): Gtk-WARNING **: cannot open display: :0.0
evolution: Fatal IO error 111 (Connection refused) on X server :0.0.



```

anyone seen this before?

---

### Post by reedk on 2010-06-20
I checked and I don't have error messgaes like you do. have you checked fur PolicyKit bugs in LaunchPad? 
Offtopic: Ubuntu has a lot of polish, good fit and finish, for a Linux desktop. What it lacks is stability and consistency. And if it weren't for the family getting used to Gnome while I avoided the 4.0 evolution, I'd have KDE on their desktop as well (and not have this problem).

---

### Post by reloweb on 2010-06-27
> **reedk said:**
> Try removing the date/time applet from your panel and trying again. This worked for me (at the cost of no longer having the date displayed). If that does it for you too I will file a bug.
Yes the problem is in the date/time applet...

---

### Post by reloweb on 2010-06-27
I've opened a new bug on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/599140](https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/599140)

---

