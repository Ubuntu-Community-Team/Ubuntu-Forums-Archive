---
title: "What happened to fast user switching?"
date: 2009-11-08
forum: Desktop Environments
---

### Post by platykurtic on 2009-11-08
Back in jaunty fast user switching worked great. I use different sessions so that my girlfriend and I can have different things going on. In jaunty it was two clicks to switch between users once you turned off passwords. You just clicked on your name in the taskbar and got a list of the other logged in users. Now I just get an option to go to the login screen, which takes a bit to load, and the experience is overall just worse. Is there a way to get the old fast user switching behavior back?

---

### Post by nikko on 2009-11-17
Hi,

Karmic now use new version of gdm by default ([http://live.gnome.org/GDM/NewDesign](http://live.gnome.org/GDM/NewDesign) ) which has some limitations/bugs (few configuration options) 

And there are two problems which make fast user switching not realy fast : 
[LIST=1]
[*]users' list : applet can't get user list from gdm (see this [bug]("https://bugs.launchpad.net/ayatana-ubuntu/+bug/438720") )
[*]locking : when a new session is created, gdmflexiserver is launched. During rewrites, options not to lock screen disappeared (see this [upstream bug]("https://bugzilla.gnome.org/show_bug.cgi?id=559623") )
[/LIST]

Regarding first problem, we can wait and hope it'll be solved for 10.04. And use Ctrl+F7, Ctrl+F9... to switch console (it'll bring memories).

Regarding second problem, I fear gnome team are not really interested in fixing this bug (they did not include patches from Dan Nicholson nor made any comment).
I changed gdmflexiserver code so that it never locks current session. I mean at home I don't really care about locking session, and I still can lock my session on demand.

Nikko

---

### Post by BlackShift on 2010-05-14
The 'wishlist' bug report for Lucid is here:
[https://bugs.launchpad.net/ubuntu/+s...on/+bug/501864](https://bugs.launchpad.net/ubuntu/+s...on/+bug/501864)

I added a comment there on how I fixed it by disabling locking the screen entirely by using gconf-editor to set /desktop/gnome/lockdown/disable_lock_screen to True.

That way it is not possible to lock the screen at all anymore, but that is fine for me.

Another way is to setup the login to not require a password and use 'Switch From ..' to switch users, but this is slightly slower.

---

