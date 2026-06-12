---
title: "How to turn off inactive mouse pointer in kde?"
date: 2008-02-14
forum: Desktop Environments
---

### Post by flightless bird on 2008-02-14
I would like to turn off or hide the mouse pointer when inactive for a couple of minutes - I have been using compiz-fusion advanced zoom to zoom in on internet flash videos but the pointer sits annoyingly in the middle of the screen - is there anyway for it to get the hint and disappear when inactive?

---

### Post by RedSquirrel on 2008-02-14
If KDE doesn't provide that sort of thing, you could try **unclutter**. It's in the repositories. Then just read the manpage (man unclutter).

Here's mine for example:

```
unclutter -root -idle 12 &
```

---

### Post by avdzm on 2008-02-14
cool thanks for the tip,
will give it a try... :)

---

### Post by flightless bird on 2008-02-15
Wonderful, just what I was looking for. Cheers

---

