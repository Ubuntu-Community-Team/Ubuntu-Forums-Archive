---
title: "DOS Games help"
date: 2009-03-15
forum: Gaming &amp; Leisure
---

### Post by warekl on 2009-03-15
I have just installed DOSBOX and mounted a drive..my problem is how to extract or install dos games into that folder. When I try to run an install.bat file or install.exe, I don't get the games to install so I don't know how to install the games themselves....
Thanks
Keith

---

### Post by grossaffe on 2009-03-15
make sure you are running said files in DOSbox

---

### Post by warekl on 2009-03-15
> **grossaffe said:**
> make sure you are running said files in DOSbox
Now I'm having more issues, opened DOSBOX and tried to mount my drive and keep getting the "Directory doesn't exist" message..
In my Home directory I have a folder dgame and within that one called qfg3.
Dosbox won't let me....mount c /home/dgame/qfg3/  or mount c /home/dgame/  it will only let me mount c /home/  and no deeper...any idea?
Thanks
Keith

---

### Post by Perfect Storm on 2009-03-15
You might try Dosbox Game Launcher (DBGL): [http://members.quicknet.nl/blankendaalr/dbgl/](http://members.quicknet.nl/blankendaalr/dbgl/)
I find it easier to handle many dos games.

---

### Post by killerdogg77 on 2009-03-16
try this worked for me  [http://www.dosgames.com/forum/post-93360.html](http://www.dosgames.com/forum/post-93360.html)

---

### Post by R33D3M33R on 2009-03-16
> **warekl said:**
> Now I'm having more issues, opened DOSBOX and tried to mount my drive and keep getting the "Directory doesn't exist" message..
In my Home directory I have a folder dgame and within that one called qfg3.
Dosbox won't let me....mount c /home/dgame/qfg3/  or mount c /home/dgame/  it will only let me mount c /home/  and no deeper...any idea?
Thanks
Keith

This is because the path is not correct. It must be:

```
mount c /home/username/dgame/qfg3/
```

Replace username with your username and it should work!

---

### Post by warekl on 2009-03-18
> **R33D3M33R said:**
> This is because the path is not correct. It must be:

```
mount c /home/username/dgame/qfg3/
```

Replace username with your username and it should work!

Perfect! Thanks!

---

