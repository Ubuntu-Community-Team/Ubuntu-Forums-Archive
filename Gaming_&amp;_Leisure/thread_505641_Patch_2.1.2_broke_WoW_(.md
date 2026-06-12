---
title: "Patch 2.1.2 broke WoW :("
date: 2007-07-20
forum: Gaming &amp; Leisure
---

### Post by daynah on 2007-07-20
I havent gotten to play in a while' so this may be an old patch. But it told me to restart, sure, it started downloading, then it tried to install the patch but it never got ang where saying ti was waiting for all of the files to close. All of the other times, if I remember right, the full screen part had gone away, but this time it hadn't. The installer never finished and then froze.

It's patch 2.1.2, Feisty, with Wine on a Nvidia card. Any pointers? :)

---

### Post by CJNyfalt on 2007-07-20
Well, I also have patching problems. I'm not sure this is the same issue, but here's what I did:
Main game (WoW.exe) froze when I clicked the restart button. I pressed Ctrl+Alt+F1 and opened the console, killed WoW.exe. The downloader for the patch itself was not affected and continued running. So I was able to update the game. Still have some occasional problems with the launcher so I run WoW.exe directly.

---

### Post by dutchman72 on 2007-07-20
i have run WoW in Cedega ever since i found it, since i always had video issues in wine, but on some patches i run into the freeze up and have learned to close out all Wine based processes and manually run the patch from command line using the Wine command after cding into the World of Wacraft directory. It always works and then tries to start up in Wine. This is where I shut it back down and go back to Cedega, you will probably just keep going there. 

And like the second poster I have learned to stay away from the launcher, run the wow.exe directly, causes less trouble.

---

### Post by daynah on 2007-07-20
> **CJNyfalt said:**
> Well, I also have patching problems. I'm not sure this is the same issue, but here's what I did:
Main game (WoW.exe) froze when I clicked the restart button. I pressed Ctrl+Alt+F1 and opened the console, killed WoW.exe. The downloader for the patch itself was not affected and continued running. So I was able to update the game. Still have some occasional problems with the launcher so I run WoW.exe directly.

That worked perfect! For terminal idots, I went to System Monitor and KILLED the app from there. Stopping didn't do it and I didn't read your instuctions well enough. ;) When I killed it, the patch went though like a charm. Thanks!

---

### Post by CJNyfalt on 2007-07-21
> **daynah said:**
> That worked perfect! For terminal idots, I went to System Monitor and KILLED the app from there. Stopping didn't do it and I didn't read your instuctions well enough. ;) When I killed it, the patch went though like a charm. Thanks!

Glad I could be of help.
I'm on the other hand is a GUI idiot. :) How do I get out of a fullscreen app that has stopped responding without killing the X server or switching to the console?

---

### Post by Ardrias on 2007-07-21
Well you could press ALT+F2 to bring up the gnome-launcher, and run wineserver -k, to kill all Wine apps.

---

