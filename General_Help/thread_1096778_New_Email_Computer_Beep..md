---
title: "New Email Computer Beep."
date: 2009-03-15
forum: General Help
---

### Post by LiamWilson on 2009-03-15
Hey all, this fix shouldn't take long, but whenever I get new email notification from evolution, my sytem beeps too. How can I turn this off, as it's annoying me. 

Tar.

---

### Post by drs305 on 2009-03-15
Try System > Preferences > Sound, Sounds tab. Check the "New email" setting and alter accordingly.

---

### Post by damis648 on 2009-03-15
Also, if you want to disable system beep altogether, open a terminal and:
```
sudo rmmod pcspkr
```
and then if that works,
```
gksudo gedit /etc/blacklist
```
and pop in a new line:
```
blacklist pcspkr
```

---

### Post by drs305 on 2009-03-15
Forgot to mention: 
Another option is within Evolution itself. Edit > Plugins > New Mail Notification. There is a sound option there as well.

---

### Post by LiamWilson on 2009-03-15
Yeah, that worked perfectly, thanks!

---

