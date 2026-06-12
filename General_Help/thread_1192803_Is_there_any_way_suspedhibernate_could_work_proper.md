---
title: "Is there any way susped/hibernate could work properly under ubuntu?"
date: 2009-06-20
forum: General Help
---

### Post by jasreca on 2009-06-20
It seems to work w/out problems while saving to disk and waking up, but after it restores gnome this "Shut down the Computer" dialog with shutdown options just keeps popping out and I can't close it or do anything with it, it just floods and keeps reopening, AWN goes crazy because of so many instances, and the systems is unusable, so all I can do is restart...

Help?

---

### Post by jasreca on 2009-06-20
I found this message after wakeup:

```
[  119.817793] Corrupted low memory at c000e3cc (e3cc phys) = 00004000
[  119.817853] Memory corruption detected in low memory
```

Wonder if that has something to do with it, and what could be causing this error...

---

### Post by jasreca on 2009-06-20
I am seriously starting to believe that this is a gnome issue...

---

### Post by jasreca on 2009-06-22
Mystery SOLVED. 

The problems for me was that I was suspending the computer using the Fast User Switch Applet which, according to some bug reports, has issues with flushig user input or something.

If I suspend using the Shutdown Applet or if computer suspends by timeout set under Power Settings - peaches. :)

---

