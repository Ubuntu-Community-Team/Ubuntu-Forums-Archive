---
title: "GNOME/Openbox not working in 9.04"
date: 2009-04-29
forum: Desktop Environments
---

### Post by mrcheesypants on 2009-04-29
I prefer to use openbox over metacity. Only problem is that ever since I installed Jaunty, I get this error in xsession-error when I try to boot into GNOME/Openbox
```

** (gnome-session:12712): WARNING **: Unknown option --choose-session=openbox-session

```

Any ideas on how to fix this?

---

### Post by mrcheesypants on 2009-04-29
bump

---

### Post by gabello on 2009-05-05
happens the same here

---

### Post by Fortuneosarcasm on 2009-05-08
You can fix it with the following:

comment out the default line and replace it with the following in /usr/bin/openbox-gnome-session
 #exec gnome-session --choose-session=openbox-session "$@"
exec gnome-session "$@"


from: [https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/272418](https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/272418)

---

### Post by HunterThomson on 2009-05-27
That didn't work for me or many other people.

I just added this to 

System/preferences/Startup Applications

```
openbox --replace 
```

Then just lunch gnome as normal.

---

