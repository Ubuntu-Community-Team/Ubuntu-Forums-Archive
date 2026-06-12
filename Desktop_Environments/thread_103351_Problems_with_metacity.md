---
title: "Problems with metacity"
date: 2005-12-13
forum: Desktop Environments
---

### Post by daedalusman on 2005-12-13
Well I was trying to change my metacity theme just a couple of minutes ago and ended up lossing the window borders. Programs will run but the borders are gone, I tried restart to see if that would fix things but alas it did not. Can someone help me with this as its kinda hard to use gnome without the borders? I tried opening the system monitor to see if metacity was still running but it would not open. This is a very strange problem and I have no idea how to fix it. All I did was try to change the metacity theme. Thanks for any help and let me know if you need some more info.

---

### Post by pmj on 2005-12-14
Did you already try to switch to another theme?

---

### Post by coldwater on 2005-12-14
you can use 

```
 psa aux | grep metacity 
``` 

to see if metacity is running.

---

### Post by daedalusman on 2005-12-14
Thanks for help, I got metacity back. It wasn't running and when I restarted my session was being saved so it wasn't starting up and restart so ran the binary and that got it going so that it would start upon restart again. I guess that theme just has some problems with metacity and I will just have to uninstall it, oh well.

---

