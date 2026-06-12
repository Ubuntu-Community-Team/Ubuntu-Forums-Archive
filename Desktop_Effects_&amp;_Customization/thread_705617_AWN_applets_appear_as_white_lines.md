---
title: "AWN applets appear as white lines"
date: 2008-02-23
forum: Desktop Effects &amp; Customization
---

### Post by ventu on 2008-02-23
Hello  Ubuntu forums.

I' have an on going issue with AWN-extras.  I guess thats what you would call this problem.  I havn't really done much with this untill I read this 'How To' [http://ubuntuforums.org/showthread.php?t=572019]("http://ubuntuforums.org/showthread.php?t=572019").

I've been scanning all through Google and the AWN forums and I nothing has worked yet. Every applet in my AWn installation is bad, I can't even remove it form the list.  Only time it goes away is if I use this command : sudo apt-get remove awn-applets-bzr.  Tihs is my AWN started from a terminal and me trying to add in some applets:
[PHP]ventu@ventu-laptop:~$ avant-window-navigator
Screen is composited.
APPLET : /usr/local/lib/awn/applets/taskman.desktop
Creating new applet :None uid:None
Creating new applet :/usr/lib/awn/applets/awnterm.desktop uid:1203799063

** (awn-applet-activation:13442): WARNING **: This desktop file does not exist None


** (awn-applet-activation:13444): WARNING **: This desktop file does not exist /usr/lib/awn/applets/awnterm.desktop


(avant-window-navigator:13432): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(avant-window-navigator:13432): GLib-GObject-CRITICAL **: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed

(avant-window-navigator:13432): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(avant-window-navigator:13432): GLib-GObject-CRITICAL **: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
Creating new applet :/usr/lib/awn/applets/awnsystemmonitor.desktop uid:1203799065

** (awn-applet-activation:13446): WARNING **: This desktop file does not exist /usr/lib/awn/applets/awnsystemmonitor.desktop


[/PHP]

For some reason they didn't get installed.  I've been hereing about a Trevino's repo but i have yet to find the link to it.

I've also tried around on these websites and still nothing:
[http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=1500](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=1500)
[http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=226](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=226)

Thanx guys

---

### Post by ventu on 2008-02-23
bump..

---

### Post by Goronok on 2008-02-23
I'm having this same issue with awn-curves. (7.10)  Anyone have any insight on this issue?

---

### Post by carlinuxlearner on 2008-02-25
I am also having the same problem. Running Ubuntu 7.10 64bit. All the applets show up as white lines, none of them work. Heres what it says in the terminal
```
** (awn-applet-activation:19058): WARNING **: This desktop file does not exist /usr/lib/awn/applets/trash.desktop

```

C@RL

EDIT::

After completely removing AWN (make sure it's gone by running this in the terminal "avant-window-navigator", if it doesn't run then it's not installed), I did a reinstall with the instructions from here [http://ubuntuforums.org/showthread.php?t=572019](http://ubuntuforums.org/showthread.php?t=572019) 
and every thing is working fine. 

Oh and please note this was with awn-curves.

C@RL

---

