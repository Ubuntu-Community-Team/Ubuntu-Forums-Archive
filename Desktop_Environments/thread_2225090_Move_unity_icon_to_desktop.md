---
title: "Move unity icon to desktop?"
date: 2014-05-19
forum: Desktop Environments
---

### Post by s9032g@comcast.net on 2014-05-19
After a lot of trouble, including wiping my SSD, I am up and running with 14.04. Happy to be so.

I would like to move some major programs from the Unity bar to the desktop. Tried the usual ways with no success so far.

Ideas? based on your own success.

Thanks

I have all the TWEAK programs

---

### Post by ka55o5 on 2014-05-19
> **s9032g@comcast.net said:**
> After a lot of trouble, including wiping my SSD [..]
Just btw., "Erasing an SSD drive not only sanitizes the drive, but recovers lost performance on systems with inefficient garbage collection" (just) in case [TRIM]("http://lifehacker.com/5640971/check-if-trim-is-enabled-for-your-solid-state-drive-in-windows-7") hadn't been active, or something: 
[http://www.cnet.com/how-to/how-to-securely-erase-an-ssd-drive/](http://www.cnet.com/how-to/how-to-securely-erase-an-ssd-drive/)
[http://www.pcworld.com/article/2088341/how-to-restore-your-ssd-to-peak-performance.html](http://www.pcworld.com/article/2088341/how-to-restore-your-ssd-to-peak-performance.html)
& Samsung SSD Magician @
[http://www.techspot.com/downloads/5345-samsung-ssd-magician.html](http://www.techspot.com/downloads/5345-samsung-ssd-magician.html)

> **s9032g@comcast.net said:**
> I have all the TWEAK programs
As in?..:)

---

### Post by deadflowr on 2014-05-20
> I would like to move some major programs from the Unity bar to the desktop. Tried the usual ways with no success so far.

Which usual ways.
It helps to know...

Otherwise, we could be going around in circles with bad advice.

---

### Post by xREDEMPTIONx on 2014-05-20
You can use Nautilus (file manager) to navigate to /usr/share/applications. Then just copy/paste from the Nautilus window to your desktop.

---

### Post by s9032g@comcast.net on 2014-05-20
The usual steps involve things like drag and drop which used to work. Here is what I have tried;

Drag from Dash to desktop: throws an error.
Right-click on the icon in the Dash: opens a second information canvas, but still no option to create an icon.
Start the program, right-click in the launcher: still no option to create a canvas.

--One I have not tried because I don't have nautilus is this one. Others say it fails:
Open the "Desktop" folder in Nautilus (located in the Home directory), drag the program from the Dash to the file browser to the desktop: same error as dragging from the dash to the desktop.

I don't have Nautilus. I am willing to get it (and I think I know how to use it) I see 4 entries for Nautilus in Ubuntu Software. Actions Config Tool; Pastebin; Compare ext prefs; and Scripts Mgr. Which one(s) do I want?

---

### Post by deadflowr on 2014-05-20
Nautilus is the default file manager for Ubuntu.
Unless you changed it to another, you have it installed and are currently using it.

Post #4 is the simplest way to add launcher to the desktop.
You have to right-click copy right-click paste.
Drag and drop no longer works.

To wit, the folder which contains launchers is /usr/share/applications
simply right-click copy, then  navigate to your Desktop folder and right-click paste.

---

### Post by s9032g@comcast.net on 2014-05-21
OK & Thanks!

    When I looked for Nautilus as an installed package it came up zip, so, being very literal I looked in Ubuntu Software and found 4 possibilities.

    The commands needed to move an icon to the desktop are: Files (right on the Unity bar)/Computer/Usr/share/applications/. Find the icon/ right click/move to desktop.

   This is about 7 steps to do something that used to be accomplished by a simple drag and drop. Is that a move in the right direction (improvement?). Maybe it was an oversight. The more complicated something is the less free it is.

   Love this forum.

---

### Post by grumblebum2 on 2014-05-21
Another method is if you have gnome-session-flashback installed, run gnome-panel in the ubuntu/unity session and 
drag and drop from it's applications menu.
Can do the same from cairo-dock.

---

### Post by s9032g@comcast.net on 2014-05-23
Thanks. I don't have these items. I really don't want that many things on the desktop, just the few things I use the most (no sense leaving the desktop blank just because I have Unity. The job is done.

---

