---
title: "[SOLVED] Help  updating Unreal Tournament 2004."
date: 2007-08-22
forum: Gaming &amp; Leisure
---

### Post by aberadam on 2007-08-22
I've recently installed UT2004, everything's fine.  When I tried to play online I was told I needed to update the client. So I've downloaded something called the 'megapack' which supposedly has everything I need.

Now I have this 200 meg tarball sat on my desktop and don't know what to do with it.  Presumably extract it somewhere, but where?  What about permissions in the filesystem?  I've checked and there are no instructions included. 

Thanks.

---

### Post by aberadam on 2007-08-22
I tried extracting it to the appropriate place: 

> You don't have the right permissions to extract archives in the folder "/usr/local/games/ut2004"

---

### Post by Freddy on 2007-08-22
You would need to have root privileges to extract the files into your /usr/local, fire up you filemanager  as root with.
```
gksu "fm"
```
Where "fm" is your filemanager of choice, copy the files into the appropriate folder and answer "yes to all" when "you are about to overwrite" comes.

---

### Post by _simon_ on 2007-08-22
All you actually need is to patch it to the latest version - 3369-2

[http://treefort.icculus.org/ut2004/ut2004-lnxpatch3369-2.tar.bz2](http://treefort.icculus.org/ut2004/ut2004-lnxpatch3369-2.tar.bz2)

Just download that, extract it and copy the files into your UT2004 folder.

As above, as you've installed it to that location you need root so gksudo nautilus from terminal will do it.

---

### Post by aberadam on 2007-08-22
Thanks guys, but filemanager of choice?  Nautilus?

---

### Post by _simon_ on 2007-08-22
Yes - gksudo nautilus

---

### Post by aberadam on 2007-08-22
Thanks, I do that, which shows this in the terminal: 

> adam@adam-desktop:~$ gksudo nautilus
Initializing gnome-mount extension

Then a new file manager window opens with a filing cabinet icon in the corner (that may not be standard I have non-standard theme), but the 'megapack' is gone.  It won't show up in that new window.

---

### Post by aberadam on 2007-08-22
If I open if a new window which can see the megapack it won't extract to UT2004 because I don't have permission.

---

### Post by _simon_ on 2007-08-22
Extract the megapack to desktop or something and open a normal nautilus window to view that.

Then open a root nautilus (gksudo nautilus), - so you should now have 2 windows open side by side-  locate your UT2004 directory in the root nautilus then I think you can just drag and drop into place - if not then copy paste.

---

### Post by aberadam on 2007-08-22
The new window that pops up after gksudo nautilus doesn't show my home folder.  Just the file system, desktop (with nothing in it), and 'root' (I did that folder I think).

---

### Post by Freddy on 2007-08-22
If you extracted your megapack onto you desktop, you will find it with your root filemanager at /home/user/Desktop.

---

### Post by aberadam on 2007-08-22
Great, thankyou very much, all working.

---

