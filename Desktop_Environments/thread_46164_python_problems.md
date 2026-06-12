---
title: "python problems"
date: 2005-07-03
forum: Desktop Environments
---

### Post by vaskark on 2005-07-03
Many programs require PyGTK to work. Does python2.4-gtk2 satisfy this? I'm really having a terrible time with apps that use python. For instance, the music app Quod Libet gives me this error:

 > Traceback (most recent call last):
  File "/usr/bin/quodlibet", line 333, in ?
    import gtk
ImportError: No module named gtk 

Winki the Ripper gives me this:

 > Importing module gtk...
Sorry. Your PyGTK installation does not seam to be correct

These apps use to work fine. Can someone point in the right direction? If I do need to compile PyGTK myself (from [www.pygtk.org]("http://www.pygtk.org")) i'll have to keep trying to get through to the site - can't seem to connect to them.

Thanks!

---

### Post by vaskark on 2005-07-03
*bump* Somebody! Please!

---

### Post by npaladin2000 on 2005-08-11
You need the -dev package.

I believe it's called python2.4-gtk2-dev.  There's also a python2.4-gnome-dev or something that shouldn't hurt either.

---

### Post by vaskark on 2005-08-11
[QUOTE=npaladin2000]You need the -dev package.

I believe it's called python2.4-gtk2-dev.  There's also a python2.4-gnome-dev or something that shouldn't hurt either.[/QUOTE]
And where would I find these packages? They're not showing up in Synaptic. I also searched the Hoary packages database and google. Can you point me to where I might find them?
Thanks.

---

