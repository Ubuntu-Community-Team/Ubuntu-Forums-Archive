---
title: "[SOLVED] sudo just says password is incorrect"
date: 2008-12-15
forum: General Help
---

### Post by leveliv on 2008-12-15
```
chris@chris-laptop:~$ sudo apt-get install program
Sorry, try again.
Sorry, try again.
Sorry, try again.
sudo: 3 incorrect password attempts

```

This is what I get when I try to do something as root..I don't even get prompted for a password it just goes right to that.

I know exactly what I did. I recently install my fprint reader so I had to edit my common-auth file. I ended up ## to lines that werent supposed to be apparently. 

If I could edit that file I would be fine. Is there a possible way to edit a file without being able to be root?

---

### Post by NSAJEFF on 2008-12-15
You could try booting from the liveCD to modify those files. It's quick and dirty but it'll get the job done. Goodluck.

---

### Post by oldos2er on 2008-12-15
Boot into recovery mode, and use nano to edit the file.

---

### Post by leveliv on 2008-12-15
didnt think about the liveCd ...Thank you...I never really did like using recovery mode. but I could give that a shot too

---

