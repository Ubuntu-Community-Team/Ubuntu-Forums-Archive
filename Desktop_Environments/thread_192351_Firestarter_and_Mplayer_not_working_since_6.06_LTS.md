---
title: "Firestarter and Mplayer not working since 6.06 LTS upgade"
date: 2006-06-08
forum: Desktop Environments
---

### Post by xs1 on 2006-06-08
Since upgrading to Ubuntu 6.06 LTS, from 5.10 Mplayer and Firestarter no longer start.
When the icon for Firestarter is clicked, it shows "starting firestarter" in the task bar but it then closes itself down. This previously used to autostart on logon to Ubuntu, with the following line in addtional startup programs

sudo firestarter start --hidden

it no longer autostarts or starts if you try to manually launch it, The same fault also occurs with Mplayer. I have removed and reinstalled both packages via apt-get and synaptic with no joy.
Any idea how I can get these 2 programs working again ??

EDIT

It appears Firestarter is working but the GUI is unable to load, running firestarter from the terminal gives

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:5530): Gtk-WARNING **: cannot open display:

I can get this working with the workaround found when searching the forum, but this needs to be done on every boot. in teminal type  *host +local: *
MPlayer just does not want to work on launch it throws up an error box that disappears too quickly to view.

---

### Post by suvantoj on 2006-06-13
I also have the same problem, though only with Firestarter. MPlayer works fine.

---

### Post by Yleeyas on 2006-06-13
Hi xs1,

I have the same problems with firestarter and I use the same 'xhost +local:' workaround. I'm following the bug report (47662), but this seems to be in limbo for now.

With the mplayer problem, can we get more info. Try running it in a terminal window to see what errors are generated, and post them here.
(in terminal window run the gui version with eg:
$> gmplayer /home/video/file.mov)

Yleeyas

PS. I had the same problem with mplayer and found I had to reinstall mplayer-skins using synaptic. You may want to try that too.

---

