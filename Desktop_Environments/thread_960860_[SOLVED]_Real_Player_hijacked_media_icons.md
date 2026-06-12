---
title: "[SOLVED] Real Player hijacked media icons"
date: 2008-10-27
forum: Desktop Environments
---

### Post by x1a4 on 2008-10-27
Hi,
I installed Real Player 11, tried it, didn't like it, purged it, but the media files icons set by RP11 continue to be those ugly Real Player icons.  How do I fix this, and use my icon theme's icons for media files?  

I already tried switching icon themes hoping this would fix it, but it didn't.  No matter which icon theme I use, icons for media files are always Real icons. 

Thank you.

---

### Post by mouseboyx on 2008-10-27
re-install themes, or reinstall your default player, might work.

---

### Post by x1a4 on 2008-10-27
Nope.

---

### Post by mouseboyx on 2008-10-27
all the icons should be in /usr/share/pixmaps, im not sure how to change the default icons in the first place...

---

### Post by x1a4 on 2008-11-14
bump

---

### Post by cardinals_fan on 2008-11-16
[http://ubuntuforums.org/showthread.php?t=809569](http://ubuntuforums.org/showthread.php?t=809569)

Google is the best :D

---

### Post by -Leo- on 2008-11-17
More specifically: [http://ubuntuforums.org/showpost.php?p=5081742&postcount=5](http://ubuntuforums.org/showpost.php?p=5081742&postcount=5)

And one user reports it not working in Thunar (which I'm guessing you're using), which was true for me as well when I simply ran the script.  Though when I ran the script as root (sudo ./fixicons.sh), it worked flawlessly.

---

### Post by x1a4 on 2008-11-20
> **cardinals_fan said:**
> [http://ubuntuforums.org/showthread.php?t=809569](http://ubuntuforums.org/showthread.php?t=809569)
This isn't it. 

> Google is the best :D
Not in this case.  I have googled for this, but didn't find the answer.

---

### Post by x1a4 on 2008-11-20
> **-Leo- said:**
> More specifically: [http://ubuntuforums.org/showpost.php?p=5081742&postcount=5](http://ubuntuforums.org/showpost.php?p=5081742&postcount=5)

And one user reports it not working in Thunar (which I'm guessing you're using), which was true for me as well when I simply ran the script.  Though when I ran the script as root (sudo ./fixicons.sh), it worked flawlessly.

Not in my case it didn't.  

Anyway, I solved it.  Removing ~/.local/share/icons/ra_hicolor/ did the trick.

---

