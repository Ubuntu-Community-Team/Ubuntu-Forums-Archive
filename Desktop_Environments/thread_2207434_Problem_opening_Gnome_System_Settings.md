---
title: "Problem opening Gnome System Settings"
date: 2014-02-23
forum: Desktop Environments
---

### Post by ahamdi on 2014-02-23
Hi
I have a strange problem and I could not figure out what caused it .
When I try to open Gnome System Settings, nothiong happens.
I tried to use the Terminal and got the following error ouitput :
```
(gnome-control-center:4892): GLib-GObject-WARNING **: cannot derive 'GnomeControlCenter' from non-fundamental parent type 'CcShell'

(gnome-control-center:4892): GLib-CRITICAL **: g_once_init_leave: assertion 'result != 0' failed


(gnome-control-center:4892): GLib-GObject-CRITICAL **: g_object_new: assertion 'G_TYPE_IS_OBJECT (object_type)' failed
Segmentation fault (core dumped)



```

My laptop is a Toshiba Satellite A 350
```
$> cat /etc/lsb-release DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.10
DISTRIB_CODENAME=saucy
DISTRIB_DESCRIPTION="Ubuntu 13.10"
```

---

### Post by ahamdi on 2014-02-25
UP, does anyone have an idea how to track this ?

---

### Post by ahamdi on 2014-03-01
I've uninstalled the default Gnome settings Panel and installed the one from Unity using
> sudo apt-get install gnome-control-center-unity

But the same problem is still there . Any help is appreciated.

---

### Post by phidia on 2014-03-06
Some users with this problem report that opening control center with > MALLOC_CHECK_=1 gnome-control-center works.
If it doesn't you got a free bump anyway. There is a related bug at launchpad but try that ^ and see how it goes.

---

### Post by ahamdi on 2014-04-03
Unfortunately, the workaround didn't work
Could you point me to the Launchpad bug please!!

---

### Post by ahamdi on 2014-04-04
Here is the bug reported in launchpad [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1278209](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1278209)

---

### Post by ahamdi on 2014-04-22
This issue was work-arounded and fixed by downgrading the library version of libgnome-control-center1 from 1:3.10.1-0ubuntu1~saucy3 to 1:3.6.3-0ubuntu45
 [https://bugs.launchpad.net/ubuntu-gnome/+bug/1309419/comments/10](https://bugs.launchpad.net/ubuntu-gnome/+bug/1309419/comments/10)

---

