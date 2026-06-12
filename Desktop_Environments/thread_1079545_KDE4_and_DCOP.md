---
title: "KDE4 and DCOP"
date: 2009-02-24
forum: Desktop Environments
---

### Post by radu_radu on 2009-02-24
Hello all,
I upgraded some KDE packages a minute ago, then I started getting some weird errors when I start apps that are liked to KDE via DCOP:

First, I get a popup which sounds like this: (translated into english)

[B]Could not read network connection list.
/home/radu/.DCOPserver_Xanadu__0
Verify that "dcopserver" is working!
[/B]

/home/radu/.DCOPserver_Xanadu__0 does not exists.

when I try to run kdeinit, or dcopserver directly, I got this:

```
radu@Xanadu:~$ kdeinit
/usr/bin/iceauth:  error in locking authority file /home/radu/.ICEauthority
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPServer self-test failed.
ICE Connection rejected!

iceauth:  error in locking authority file /home/radu/.ICEauthority
kdeinit: DCOPServer could not be started, aborting.

```

As a side effect, some apps like amarok don't get their icons in the tray anymore, they float in a miniature window on the desktop. Also, amarok lost all its cache, and I had to rescan the music folder and add all the covers again.

Any tips on how to solve this?
Any hints?

---

### Post by radu_radu on 2009-02-24
More data:
I ran kdeinit4 in the terminal, like below, then started amarok from the K menu. Here's the output:

```
radu@Xanadu:~$ kdeinit4
kdeinit4: Shutting down running client.
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
kdeinit4: preparing to launch /usr/bin/kded4
KDE Daemon (kded) already running.
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...

radu@Xanadu:~$ kdeinit4: preparing to launch /usr/bin/amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
/usr/bin/iceauth:  error in locking authority file /home/radu/.ICEauthority
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ICE Connection rejected!

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPServer self-test failed.
iceauth:  error in locking authority file /home/radu/.ICEauthority
kdeinit: DCOPServer could not be started, aborting.
I couldn't enable notifications at the dcopserver!
DCOPRef::send(): no DCOP client or client not attached error
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)

```
 (at this point, amarok runs in foreground)

---

### Post by radu_radu on 2009-02-25
Solved.
For some reason, /home/radu/.ICEauthority (which is a file) turned itself into an empty directory, and dcop couldn't overwrite it. So I deleted it by hand, and all my problems are gone.
Also, on a quick overview of the net, it seems that amarok has a tendency to screw around with dcop, and there's a lot of complains about it (soon to be gone, since there's an amarok 2 which uses directly dbus)

---

### Post by unelsson on 2009-03-29
I've got the same problem, however, none of the solutions presented on forum's work. All in all, my system is breaking up as a whole. All of the symptoms started around the same time, couple of days ago, possibly related with video-editing with Kino (at least I can say for certain that amarok-trouble started when Kino crashed). I'm using Ubuntu and Gnome, but I have a few programs designed for kde.

amarok: Does open up a miniature window without any buttons, can't do anything with amarok currently. The error at startup: "Could not read network connection list /home/nelsson/.DCOPserver_nelsson-desktop__0"

amsn: Crashes horribly after some time of use, starts to output errors on every action. If I try to kill the process via console, the process disappears from process list, but the window and the program stays floating.

pidgin: Starts, but crashes quickly after startup. Shuts itself down.

firefox: back-button is gray (unclickable) all the time, googling via search bar doesn't work.


Ok.. More info about the problem. It seems that rebooting the computer removes the problems. I also purge removed amsn. Firefox search bar still doesn't work, although most of the problems are gone.

---

