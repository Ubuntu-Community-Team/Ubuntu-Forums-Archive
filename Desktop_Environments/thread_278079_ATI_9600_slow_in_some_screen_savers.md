---
title: "ATI 9600 slow in some screen savers?"
date: 2006-10-15
forum: Desktop Environments
---

### Post by Kobalts on 2006-10-15
Using gnome, and installed the latest ATI drivers, everything checks out.
fglrxinfo reports what it should, (ati..radeon 9600 ..8.29.6)
glxinfo |grep direct reports 'direct rendering: Yes',  glxgears -printfps shows average of around 100FPS.

This is on a Athlon XP 2.6 GHz,  1GB ram,9600 PRO.

Issue is that some screen savers are really slow.  It is as if it is not being accelerated at all.  I don't know which ones they are, since I set it to random.

Any ideas why some screen savers are slow?

---

### Post by kvonb on 2006-10-17
Try this:

In a terminal type the following:

sudo mkdir /usr/X11R6/lib/modules
sudo ln -s /usr/lib/dri /usr/X11R6/lib/modules/dri

Thanks to kingofsnakes2111 for this fix which worked for me :)

---

### Post by Kobalts on 2006-10-17
Hey, thanks! (to both you & kingofsnakes2111) 

That worked like a charm.  This fix needs to be sticky'ed \\:D/  Or stuck in the FAQ or something. 

Now, if someone can explain why that worked... since I don't know much about creating links to stuff.

---

### Post by kvonb on 2006-10-17
Glad it helped :)

This is the description that kingofsnakes gave:

```
There is something wrong with the path of Xscrensaver not looking
for dri in the right place (/usr/lib/dri/fglrx_dri),
instead Xscreensaver looks in /usr/X11R6/lib/modules/dri which is
non-existent.

```

However this sounds more like an ATI driver problem though, as DRI doesn't or shouldn't know anything about 3rd party video drivers.  The ATI driver should take DRI into account when it installs and make the necessary changes.

Unfortunately ATI are a little lacking in their driver department.

A link is just a shortcut to another file.


Regards, Kev :)

---

