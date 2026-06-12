---
title: "How to save openbox settings"
date: 2010-04-01
forum: Desktop Environments
---

### Post by ronnielsen1 on 2010-04-01
I've been playing with openbox and I'm really starting to like it, but it won't save my settings. I can change my wallpaper the way I want and add screenlets and wbar but it won't save. Any openbox fans out there that can give me pointers?

---

### Post by urukrama on 2010-04-01
I'm not sure what you mean by "save", but if you mean "save the session", Openbox does not do that. 

You can configure your autostart (in  ~/.config/openbox/autostart.sh) file, which tells Openbox what applications it should run whenever Openbox starts. For example, to launch wbar and set a wallpaper with feh every time you launch Openbox, make sure your autostart file looks like this:

```
#!/bin/sh 
feh --bg-scale /home/user/picture.png &
wbar &
```

For more help and information have a look at the Openbox guide linked to in my signature (it has a section on autostarting applications).

---

### Post by capngloval on 2012-03-12
I am afraid the above information is incorrect.

there is no "autostart" file in /home/user/.config/openbox/

I onnly have two files there, menu.xml and rc.xml

There is an autostart file in /etc/xdg/openbox.

I have yet to try it, so I can't tell you if this is the proper one to edit.

-Denny

---

### Post by malspa on 2012-03-12
> **capngloval said:**
> I am afraid the above information is incorrect.

there is no "autostart" file in /home/user/.config/openbox/

I onnly have two files there, menu.xml and rc.xml

I have one here, in Ubuntu 10.04:

```
steve[/media/sdb6/steve/.config/openbox]$ ls -l
total 116
-rw-r--r-- 1 steve steve  1436 Jun 22  2011 autostart.sh
-rw-r--r-- 1 steve steve 23291 Oct 30  2010 lxde-rc.xml
-rw-r--r-- 1 steve steve  3573 Jul 29  2011 menu.xml
-rw-r--r-- 1 steve steve 24056 Jun 22  2011 rc.xml
drwxr-xr-x 2 steve steve  4096 Aug  1  2011 scripts
```

I think I had to create it, though.

---

