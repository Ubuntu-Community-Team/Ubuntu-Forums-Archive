---
title: "KDE applications suddenly very slow"
date: 2006-11-04
forum: Desktop Environments
---

### Post by louis_nichols on 2006-11-04
Hi everybody!

I run Ubuntu edgy, with a mostly gnome desktop. There are some kde apps that I can't live without, like amarok, krusader and k3b, so I have always used them under gnome with very good results.

But then, yesterday, almost out of the blue, they all started running painfully slow. Like it takes 5 mins for one to start, and if I click something like a menu, it takes it 10 seconds to respond to that click.

When I start them in terminal, the output doesn't tell me anything I can interpret. Like, krusader says:
```
$ krusader
QLayout "unnamed" added to ListPanel "unnamed", which already has a layout
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
QLayout "unnamed" added to ListPanel "unnamed", which already has a layout
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
QLayout "unnamed" added to ListPanel "unnamed", which already has a layout
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found

```

and amarok puts out ```
$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow

```

kdeinit says ```
$ kdeinit
kdeinit: Shutting down running client.
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/myself/.DCOPserver_home__0
and start dcopserver again.
---------------------------------

KDE Daemon (kded) already running.
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!

```
but when I delete /home/myself/.DCOPserver_home__0 and un it again, I don't get any errors, but no improvements either

I have no idea what all this might be caused by and I would really appreciate some help, because all this is very frustrating. I tried reconfiguring and reinstalling some of the packages, but no luck.

---

