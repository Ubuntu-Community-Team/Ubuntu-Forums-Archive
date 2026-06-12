---
title: "No Sound in Flash"
date: 2006-03-01
forum: Desktop Environments
---

### Post by Das Ein on 2006-03-01
I've look through a few guides and either they didn't work, or I got errors for example when trying to edit 'esd.conf' I got this error:

> jordan@Jordan:/etc/esound$ ./esd.conf
bash: ./esd.conf: Permission denied

And my situation is a tad different than these. My sound was playing fine, I left for an hour, and now no sound in flash. I can here system sounds fine, but no flash sound.

---

### Post by Xian on 2006-03-01
[QUOTE=Das Ein]My sound was playing fine, I left for an hour, and now no sound in flash.[/QUOTE]

If sound in flash was working beforehand then it appears to be nothing more than a sound conflict between applications. There are several theads in the forum dealing with this subject.

---

### Post by Xian on 2006-03-01
[QUOTE=Das Ein]I've look through a few guides and either they didn't work, or I got errors for example when trying to edit 'esd.conf' I got this error:

jordan@Jordan:/etc/esound$ ./esd.conf
bash: ./esd.conf: Permission denied[/QUOTE]

$ sudo gnome-open /etc/esound/esd.conf

---

### Post by Das Ein on 2006-03-01
[QUOTE=Xian]If sound in flash was working beforehand then it appears to be nothing more than a sound conflict between applications. There are several theads in the forum dealing with this subject.[/QUOTE]

I have no applications using sound, nor do I have any files for them to play regaurdless ... unless XChat uses it :r.

....

Hmm I just realised I had mutlipul flash videos up (not on purpose), so never mind.

---

