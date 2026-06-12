---
title: "gnome-utils appearance"
date: 2009-02-10
forum: Desktop Environments
---

### Post by 7Sasha on 2009-02-10
[IMG]http://img7.imageshack.us/img7/3483/screenshotgz0.png[/IMG]

Some other apps looks like that also.
I can't say what exactly I've installed and what should I remove.
Counting on your help. 
Regards.

---

### Post by 7Sasha on 2009-02-11
any suggestions ?

---

### Post by KaiHeimann on 2009-02-11
Can you give us a bit more information? What were you doing just before you lost the program window? Have you tried to log off and restart x?

---

### Post by 7Sasha on 2009-02-11
I did. Anyway I can't point at anything as I found it only the next day when I turned on the PC.
=(

---

### Post by KaiHeimann on 2009-02-11
> **7Sasha said:**
> I did. Anyway I can't point at anything as I found it only the next day when I turned on the PC.
=(

Did you do a system update the day before? As it only happened after you started it up again, could that be it? You haven't got your adept manager set to automatically install patches?

---

### Post by 7Sasha on 2009-02-11
Yep I did a lot of updates the day before with that automatic updater
and some manual updates, however I'm not sure which one caused it.

---

### Post by KaiHeimann on 2009-02-11
One of the first things that I would check would be whether you got a new kernel. You can do this by entering
```
nano /boot/grub/menu.lst
```

and see whether you have a new kernel in there. If you do have another kernel listed, maybe try booting into that one through Grub and see if that fixes it. Otherwise it might be a graphics card driver if it was updated yesterday.

Let us know if any of those things help.

---

### Post by 7Sasha on 2009-02-11
Unfortunately that didn't help. Formatting and reinstalling ubuntu helped :(

---

