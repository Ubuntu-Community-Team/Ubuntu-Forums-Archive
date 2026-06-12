---
title: "d4x cant' start"
date: 2005-08-25
forum: Desktop Environments
---

### Post by xodeus on 2005-08-25
Hi guys.
I followed the installation from ubuntuguide and d4x wont start.
Here's the cmdline log.
```
mariusz@networkadmin101c:~$ d4x

(d4x:17813): Gdk-CRITICAL **: gdk_gc_set_clip_rectangle: assertion `GDK_IS_GC (gc)' failed

(d4x:17813): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:17813): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:17813): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:17813): Gdk-CRITICAL **: gdk_draw_line: assertion `GDK_IS_GC (gc)' failed

(d4x:17813): Gdk-CRITICAL **: gdk_gc_set_clip_rectangle: assertion `GDK_IS_GC (gc)' failed
Lagersegmentfejl
mariusz@networkadmin101c:~$
```

---

### Post by xodeus on 2005-08-25
Bump

---

### Post by KingBahamut on 2005-08-25
have you tried removing it. 

apt-get remove d4x 
apt-get install d4x

---

### Post by xodeus on 2005-08-25
[QUOTE=KingBahamut]have you tried removing it. 

apt-get remove d4x 
apt-get install d4x[/QUOTE]
 still the same problem

---

### Post by KingBahamut on 2005-08-25
Based on what im seeing, this looks like a GTK resize issue, Let me research a bit and see what I can dig up.

---

### Post by KingBahamut on 2005-08-25
Might need to recomplie Gtk to fix this. Hmmmmm.....

I dont have d4x installed, I always just use wget. Let me try d4x and see what I get.

---

### Post by xodeus on 2005-08-25
[QUOTE=KingBahamut]Might need to recomplie Gtk to fix this. Hmmmmm.....

I dont have d4x installed, I always just use wget. Let me try d4x and see what I get.[/QUOTE]
 It's because I'm trying to use FlashGot an extension to firefox. It does not support wget.
Are there any other downloaders in the repos?

---

