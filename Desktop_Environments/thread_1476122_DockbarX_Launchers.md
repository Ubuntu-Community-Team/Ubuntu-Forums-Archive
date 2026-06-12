---
title: "DockbarX Launchers"
date: 2010-05-07
forum: Desktop Environments
---

### Post by benmandude on 2010-05-07
I was wondering if there is any way to get different launchers for each workspace with DockbarX. For example, have chrome, songbird on workspace 1; and eclipse on workspace 2.

As of right now, the same launchers appear on each workspace. I'm not sure if this is possible just wondering if anyone has any suggestions on how to accomplish this.

---

### Post by M7S on 2010-05-07
No, you can't. Sorry.


M7S,
DockbarX developer.

---

### Post by kerry_s on 2010-05-07
> **M7S said:**
> No, you can't. Sorry.


M7S,
DockbarX developer.

any chance you could make DockbarX work in xfce4-panel with xfapplet?

---

### Post by benmandude on 2010-05-07
That's too bad, that would be a really nifty feature to have for different task oriented workspaces.

---

### Post by M7S on 2010-05-08
> **benmandude said:**
> That's too bad, that would be a really nifty feature to have for different task oriented workspaces.
I might add it in the feature. I have a lot of features with higher priority right now, but if you post a blueprint at launchpad I won't forget it.

---

### Post by M7S on 2010-05-08
> **kerry_s said:**
> any chance you could make DockbarX work in xfce4-panel with xfapplet?
It used to work. Can you run dockbarx in window to make sure it's nothing else that is wrong? ("dockbarx.py run-in-window" from a terminal)

---

### Post by benmandude on 2010-05-08
I have registered a blueprint and I believe I have put you as the assignee. I recommended a menu within the already existing properties menu of dockbarx. I thank you for your consideration of my request and hope that it you can implement it in the future. This is the first time I have actually corresponded with a developer of a feature I use. I'm very impressed with your interest in the community. Thank you.

---

### Post by kerry_s on 2010-05-08
> **M7S said:**
> It used to work. Can you run dockbarx in window to make sure it's nothing else that is wrong? ("dockbarx.py run-in-window" from a terminal)

i get this:

> 
** (dockbarx.py:11742): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (dockbarx.py:11742): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (dockbarx.py:11742): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
  File "/usr/bin/dockbarx.py", line 126, in <module>
    import Image
ImportError: No module named Image



i'm running a lubuntu 10.04 install, replaced lxpanel with xfce4-panel, replaced pcmanfm with nautilus.
in case it matters i have "recommends" turned off in synaptic.

---

### Post by M7S on 2010-05-11
Sorry for not seeing your answer before now. Try install python-imaging. Tell me if it works so it can be added to dependencies.

---

### Post by femngi on 2010-07-04
It appears python-imaging is a dependency as installing that allows dockbarx_factory.py to run in a window. Trying to add it to the xfce4-panel with xfapplet causes the applet to hang on the gnome/mouse icon indefinitely.

*EDIT: moving the applet to a different part of the dock seemed to get it working, I'm not sure why. Window previews still just show an icon.

---

### Post by jjpcexpert on 2010-12-23
I have actually got DockBarX running in Xfce. It's my favourite (notice I'm a Brit) GNOME Panel applet of all time. I WILL implode if you don't see this.

---

### Post by [Yatta] on 2010-12-29
Would you be so kind as to tell us HOW you got it to work?

---

### Post by jastonas on 2011-10-20
Interested in this... after almost one year, has anyone managed it?

---

### Post by M7S on 2011-10-20
If I have understood things correctly the xfapplet has become less stable in the last few months. I haven't tried it for myself though. You should be able to run DockbarX as a stand alone in xfce without any problems though.

---

