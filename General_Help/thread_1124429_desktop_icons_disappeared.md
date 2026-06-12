---
title: "desktop icons disappeared"
date: 2009-04-13
forum: General Help
---

### Post by ypelleg on 2009-04-13
Suddenly all my desktop icons have vanished (including mounted window disks, shortcuts etc).
Blank.....

Anyone knows what might have happened?

Pelleg.

---

### Post by ninjapirate89 on 2009-04-13
Not unless you've messed with the configuration editor.

---

### Post by Seventh Reign on 2009-04-13
This is happening in my Jaunty Beta quite frequently.  It seems to happen when I unmount my USB Drives .. but I havent confirmed that yet.

Logging out and back in brings the Icons back .. doesnt really effect anything but its annoying.

---

### Post by UbuntuNerd on 2009-04-13
launch the &#8220;Configuration Editor&#8221; by entering the following command in a terminal:
```
gconf-editor
```
when the window opens on the left navigate to: apps > nautilus > preferences:
After you select &#8220;preferences&#8221; look on the list on the right until you see the option &#8220;show_desktop&#8221; and make sure is check, but I don't think that is the problem if it happens randomly

---

### Post by ypelleg on 2009-04-14
To Ninjapirate89: I never used gconf--editor in the past so i can't have messed with that,

To UbuntuNerd: I looked as you said, but it is already checked...

Don't know where the desktop icons disappeared to.

---

### Post by yosibeck on 2009-04-14
Look if nautilus isn't uninstaled in the Synaptic Package Manager.
I once had the same problem and it turned out somehow nautilus had been uninstalled. Re-installing it brought the icons back.
Try that.

---

### Post by ypelleg on 2009-04-14
Thanks a million!!!
That did it.
On reading your post I looked in the Syn Pack Manager and indeed somehow the main nautilus package had been un-installed.
How it happened I don't know but fixing that brought the icons back.
):P

---

