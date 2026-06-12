---
title: "OpenOffice Segmentation Fault"
date: 2006-06-27
forum: Desktop Environments
---

### Post by berzerker on 2006-06-27
I've searched the forums for a bit now, but even though some seem to get sort of the same error, it's never the same set-up or there is another error message besides the segfault, but basically,  OOo is broken here. I use the lastest Ubuntu release and everything appears to be working except for OO.o. Whenever I try to run it, it just crashes before loading properly. Trying to run it from the commandline gives this error:
```
/usr/lib/openoffice/program/soffice: line 233: 22578 Segmentation fault      "$sd_prog/$sd_binary" "$@"

** (process:22565): WARNING **: Unknown error forking main binary / abnormal early exit ...
```

I have installed the Nvidia drivers and Sun's Java environment, apart from that, nothing has changed since the default installations. 

Anyone have any good ideas?

---

### Post by Saslik on 2006-06-27
I have this exact same problem. Openoffice starts if I've just recently booted the OS, but after running ubuntu for hours it won't start up.

---

### Post by kpkeerthi on 2006-06-27
I have nvidia driver (restricted) and sun java sdk too but open office seems to work fine. So the problem could be something else in your case.

---

### Post by berzerker on 2006-07-01
[QUOTE=kpkeerthi]I have nvidia driver (restricted) and sun java sdk too but open office seems to work fine. So the problem could be something else in your case.[/QUOTE]

Okay, I was thinking along those lines since they were they only real changes I've made since the initial install. 

Any idea what else can cause it then?

---

