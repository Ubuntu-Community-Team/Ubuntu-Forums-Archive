---
title: "Weird Trash problem"
date: 2006-02-10
forum: Desktop Environments
---

### Post by seakiwi on 2006-02-10
OK, so this is really weird. All of a sudden my Trash bin is broken. If I right click on any file to "move to trash"  the moving to trash progress window comes up but nothing happens. The progress indicator sits at 0 and the file doesn't move to the Trash. 

Same thing happens if I try to "empty trash" from the Trash applet icon in my system tray. Progress indicator pops up but nothing happens. 

Anybody got any clue what's up with this and how I can fix it? :-|

---

### Post by seakiwi on 2006-02-13
Can anyone help me with this please? :( 

This problem seemed to correct itself momentarily - but today it's back. I can't send **anything** to Trash. At the moment I'm getting around it by creating a new folder on my desktop - moving trash to that, then deleting the entire folder from my file manager. My Trash itself just will not work.

I have no idea how to fix this  :neutral:

---

### Post by Gorgazm on 2006-06-11
I'm having the same problem and for me, completely random.  I noticed that when the trash isn't working either is Ktorrent.

---

### Post by Mau on 2006-06-11
I had this problem when I had a ton of stuff in there.  It will go eventually.

If you want, just go into terminal and delete everything via the command line. I  think that would be: rm -r ~/.trash

---

### Post by dbasher on 2006-07-01
I had the same type of issue with my trash bin in KDE.
If I waited long enough, it would finally appear in the trash.
It was working except for the fact that it was very slow.
Found out I had an SMB share still mounted but inaccessible.
Unmouting would not work. It kept saying the Device or Resource was Busy.

So... I finally fixed it by running

```
sudo umount -l
```

That fixed my issue.

---

