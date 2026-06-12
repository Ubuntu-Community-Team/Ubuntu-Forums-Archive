---
title: "compile metacity without window preview"
date: 2011-10-26
forum: Desktop Environments
---

### Post by emirbugra on 2011-10-26
hi there. i want compile metacity with composite manager. but i dont want window preview in composite. which code controls the window preview when push ALT+TAB. i know how compile metacity. but i donw know which code must be change. please help me...

this post asks the same question for compiz.
[http://ubuntuforums.org/showthread.php?t=1218011](http://ubuntuforums.org/showthread.php?t=1218011)

but isn't there any answer...

---

### Post by emirbugra on 2011-10-26
and i'm using ubuntu 10.10 64bit, gnome 2.32... i dont like gnome3

---

### Post by crdlb on 2011-10-26
What version is the metacity source you want to compile and where did you get it?

Open src/core/screen.c and go to the meta_screen_ensure_tab_popup function (line ~1250). About 40 lines from the start of that function, change ```
      win_pixbuf = get_window_pixbuf (window, &width, &height);

```

to

```
      win_pixbuf = NULL;

```

---

### Post by emirbugra on 2011-10-27
thank you. i'm trying now.

[http://ubuntuforums.org/showthread.php?t=648364](http://ubuntuforums.org/showthread.php?t=648364)

---

### Post by emirbugra on 2011-10-27
so cute!!!! :) it done...

composite manager active and there is not window preview!!! :)

[http://imageupload.org/?d=ED843A9B1](http://imageupload.org/?d=ED843A9B1)

---

### Post by emirbugra on 2011-10-27
there is a problem :(

metacity foolish sometimes. for example:

[http://imageupload.org/?d=A7E42C051](http://imageupload.org/?d=A7E42C051)

i think that is a shadow problem. i dont know what will i do.

---

### Post by emirbugra on 2011-10-27
i find the problem. in ~/.gtkrc-2.0 file was:

gtk-menu-popup-delay = 0

i change it line:

gtk-menu-popup-delay = 50

now there is no problem :)

thanks to alll...

---

