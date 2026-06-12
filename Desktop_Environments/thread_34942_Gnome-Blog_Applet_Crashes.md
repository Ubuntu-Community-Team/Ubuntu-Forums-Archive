---
title: "Gnome-Blog Applet Crashes"
date: 2005-05-16
forum: Desktop Environments
---

### Post by gncuster on 2005-05-16
When I try and add the gnome-blog applet to the gnome panel I get the following error message:

```
The panel encountered a problem while loading "OAFIID:GNOME_BlogApplet".
Do you want to delete the applet from your configuration? 
```

When I run the gnome-blog-poster program it works without any problems at all. I tried restarting gnome and restarting the computer and nothing worked. Does anyone ways to keep debuging this?

Nate

---

### Post by JonahRowley on 2005-05-16
Unless you have programming skills, there's just not much you can do.  Unless this is a common problem, get in touch with the package maintainer and the person who actually wrote the software.  They'll ask you to get a backtrace with gdb, which I'm not sure how to do with an applet.  Maybe they'll fix the bug and send you a new package..  On the other hand, many smaller programs like applets can be personal projects, so there might not be any response at all if the author is busy.

---

### Post by gncuster on 2005-05-19
I think its an issue with the gconf schema failing to be installed so the applet is failing to load. But I checked the bugzilla and no one else is complaining about the package in ubuntu or debian's bug db. So I think its a configuration issue on my computer. 

In any case what is the best way to contact the packager?

---

### Post by avilella on 2005-09-23
It crashes on my computer also, even after a fresh Hoary install. It did happen also with Fedora some months ago. There must be something funky going on...

---

