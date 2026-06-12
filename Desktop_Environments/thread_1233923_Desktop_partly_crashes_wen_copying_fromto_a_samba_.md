---
title: "Desktop partly crashes wen copying from/to a samba share over LAN"
date: 2009-08-07
forum: Desktop Environments
---

### Post by snek on 2009-08-07
Since a few days I've been having a very strange problem I haven't seen before:
When I try to copy files from/to a Samba share on one of our servers here at work the "File Operations" window crashes and all the icons from my desktop disappear. Right clicking on the desktop doesn't do anything anymore either.

Running Jaunty fully updated
Xorg: 1:7.4~5ubuntu18
Ubuntu-desktop: 1.140
Nautilus: 1:2.26.2-0ubuntu2

Samba version on server is: 2:3.2.5-4lenny6
Yes it's running Debian Lenny, fully updated..

---

### Post by jflaming on 2009-08-07
Same error here... it's driving me nuts.  It looks like I can copy in the terminal using cp, but nautilus and the desktop crash when I drag and drop in nautilus.  
My system:  Jaunty fully updated desktop.
Target is running Jaunty server, sharing an NTFS disk.  Fully updated.

It doesn't seem to matter what files I copy, either.  It's not the 4gb crash that used to exist.

---

### Post by snek on 2009-08-10
Yeah the size of the file doesn't matter, I had it crash on a tiny .txt file too.
Not quite sure what the problem could be, will try to crash it on purpose later today and find something in the logs.

---

### Post by asmoore82 on 2009-08-10
when this happens, you should be able to Alt+F2 and run
```
nautilus
``` to recover the desktop.

I don't have a clue what the real underlying problem is though.

---

### Post by gjoellee on 2009-08-10
I see you are running nautilus 2.26.2, but in the latest version of nautilus, 2.26.3 I think there is a bugfix issue. Have you updated lately? Run the command:
```
sudo apt-get update && sudo apt-get upgrade
``` to update. Or just use the update manager (Remember to click on "Check" first).

---

### Post by snek on 2009-08-11
None of my jaunty machines have the version you are referring to. Are you sure that's correct and not for Karmic? Plus I update at least once a day, since I wrote a whole script to update & upgrade for me.

---

