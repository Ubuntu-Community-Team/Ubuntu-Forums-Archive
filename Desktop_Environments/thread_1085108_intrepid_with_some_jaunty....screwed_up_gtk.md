---
title: "intrepid with some jaunty....screwed up gtk?"
date: 2009-03-02
forum: Desktop Environments
---

### Post by ghotra on 2009-03-02
I am running interpid.  I was trying to get the newer version of gtkpod that existed in jaunty, so I added all its repositories to my sources.list.  Then I did an update and ran:

```

sudo apt-get update
sudo apt-get install libgpod4

```

This worked and I had the new version...it also did some upgrades, I think to libc6 and glib...

[http://packages.ubuntu.com/intrepid/libgpod3](http://packages.ubuntu.com/intrepid/libgpod3)
[http://packages.ubuntu.com/jaunty/libgpod4](http://packages.ubuntu.com/jaunty/libgpod4)

However, it turns out this was an extremely bad idea.  On a restart, gdm would fail to load completely.  Somehow I think that this has screwed the loading of almost all of my programs.  I tried to revert the changes with 'aptitude reinstall' (after changing my sources.list back), but I still can't get this to work.  

What can I do?!

---

### Post by Gramps on 2009-03-02
Try this

```
sudo apt-get remove libgpod4

```
```
sudo apt-get removeall
```
```
sudo apt-get install libgpod3
```

---

### Post by ghotra on 2009-03-02
Here is the solution I needed:

```

sudo apt-get install libgtk2.0-0=2.14.4-0ubuntu1

```

---

