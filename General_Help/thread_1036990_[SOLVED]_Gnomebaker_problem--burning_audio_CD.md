---
title: "[SOLVED] Gnomebaker problem--burning audio CD"
date: 2009-01-11
forum: General Help
---

### Post by scathmandra on 2009-01-11
Hello,

Running Intrepid on a Dell Inspiron 1501. I'm trying to burn mp3 files onto a blank CD using Gnomebaker. However, whenever I open up the application, I'll click on "Audio CD" and the window will close immediately. Sometimes I get so close as to to click "Burn" and see it disappear. I've tried purging it and re-installing, but to no avail. I've also reinstalled gstreamer0.10-mp3 from the Multiverse repository--no luck there either.

Is this a common problem? If it's not fixable, is there any other program that might be guaranteed to work?

Thanks.

---

### Post by TeoBigusGeekus on 2009-01-11
Try K3B.
Works like a charm for me...

---

### Post by hikaricore on 2009-01-11
I never had much luck with gnomebaker, even when I did use gnome I used k3b.

```
sudo apt-get install k3b
```

However I do believe there are extra steps needed to config it for mp3s which you can probably find the answers to elsewhere on the forums.
It's a start anyway right? :)

---

### Post by scathmandra on 2009-01-11
Ah, it worked! Thanks a lot. Now my CD player will at last be satisfied.

Thanks again, guys. Case closed.

---

