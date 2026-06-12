---
title: "my ubuntu wont load"
date: 2009-02-17
forum: Desktop Environments
---

### Post by steve789 on 2009-02-17
[IMG]http://img.photobucket.com/albums/v621/rerc85/Random/SSPX0148.jpg[/IMG]

---

### Post by pmlxuser on 2009-02-17
its loading alright but its the x-server that is not loading. try this command

```
 
$ startx 

```

and say what happens

---

### Post by steve789 on 2009-02-17
> **pmlxuser said:**
> its loading alright but its the x-server that is not loading. try this command

```
 
$ startx 

```

and say what happens

Fatal Server error:
No Screens Found

[IMG]http://img.photobucket.com/albums/v621/rerc85/Random/SSPX0163.jpg[/IMG]

---

### Post by prshah on 2009-02-17
> **steve789 said:**
> Fatal Server error:
No Screens Found

That's just "startx"; no sudo. 

If you still get the same error, post back the output of the following commands for more information about your system.

```

cat /var/log/Xorg.0.log
cat /etc/X11/xorg.conf
lspci | grep -i graphics\|video
lshw -C video
```

---

