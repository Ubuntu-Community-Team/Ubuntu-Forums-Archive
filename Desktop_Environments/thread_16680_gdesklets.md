---
title: "gdesklets"
date: 2005-02-23
forum: Desktop Environments
---

### Post by stijnb on 2005-02-23
Hi i want to install gdesklets

i did apt-get install gdesklets

and after starting gdesklets it says

```
gDesklets 0.26.2
Copyright (C) 2003, 2004 The gDesklets Team

This software is licensed under the terms of the GNU GPL.

/usr/lib/python2.3/site-packages/gtk-2.0/gtk/__init__.py:90: GtkDeprecationWarni ng: gtk.mainloop is deprecated, use gtk.main instead
  self.warn(message, DeprecationWarning)
/usr/lib/python2.3/site-packages/gtk-2.0/gtk/__init__.py:90: GtkDeprecationWarni ng: gtk.mainquit is deprecated, use gtk.main_quit instead
  self.warn(message, DeprecationWarning)
``` 

can anyone help me ?

thx

---

### Post by GilGalad on 2005-02-23
That's not an error, just some warnings...

---

### Post by Ste on 2005-02-23
Use the applications > run application from the gnome menu.

More info [here](http://www.ubuntuforums.org/showthread.php?t=3012&highlight=gdesklets)

---

### Post by bored2k on 2005-02-24
remember to get gdesklets-data

if u still dont get it to work, this method works:

dl the source package from the official website

and start compiling it , each time it shows an error, it will show the needed file, dl it

next time, it will show  a different error, dl that

eventually u can retry debian gdesklets-data and it will work

---

### Post by stijnb on 2005-02-25
thx for the quick response,

I installed gDesklets (offcourse :) ) and gDesklets-data

I installed sideStripes. 

when i ran the display the cursor did change in to a hand to drag and drop something, but when i placed it somewhere, nothing happened.

now what the reason can be?

thx again for the quick response

---

### Post by nrgtek on 2005-03-11
[QUOTE=stijnb]thx for the quick response,

I installed gDesklets (offcourse :) ) and gDesklets-data

I installed sideStripes. 

when i ran the display the cursor did change in to a hand to drag and drop something, but when i placed it somewhere, nothing happened.

now what the reason can be?

thx again for the quick response[/QUOTE]

I'm having the same problem  :-({|=

---

### Post by Xian on 2005-03-11
[QUOTE=nrgtek]I'm having the same problem  :-({|=[/QUOTE]
Are you able to run other desklets or is it just a problem with this particular one?
Try managing it with the gdesklets shell. That seems to be a nicer method.

---

