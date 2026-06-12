---
title: "Run *only* firefox"
date: 2010-09-07
forum: Desktop Environments
---

### Post by razta on 2010-09-07
Hello,
I have Ubuntu Server 10.04 minimal installed.

All I need is a browser to run, I don't need a window manager or anything else.

Does any one know how I could achieve this?

Thanks in advance! :D

---

### Post by Thelasko on 2010-09-07
Well, in theory "sudo apt-get install firefox" will install the minimum requirements to get firefox working.

Unfortunately, I think firefox requires some sort of window manager. (GTK+ and X11 specifically)

There are web browsers that don't require a window manger.  [Lynx]("http://en.wikipedia.org/wiki/Lynx_%28web_browser%29") is one such browser.

---

### Post by razta on 2010-09-07
Thanks for the reply.

In the end I installed xorg core, comes with gnome, but was a lot smaller than I expected.

---

### Post by beren.olvar on 2010-09-07
I think that if the only thing you want to execute on your X session is firefox, you can create a ~/.xinit file with nothing but
```

exec firefox

```
That will not load anything but the X server and firefox. Quitting firefox will also quit X.

---

### Post by shawnhcorey on 2010-09-07
> **razta said:**
> Hello,
I have Ubuntu Server 10.04 minimal installed.

All I need is a browser to run, I don't need a window manager or anything else.

Does any one know how I could achieve this?

Thanks in advance! :D

go to Google and search for "text browser".  There is a number of them.

---

