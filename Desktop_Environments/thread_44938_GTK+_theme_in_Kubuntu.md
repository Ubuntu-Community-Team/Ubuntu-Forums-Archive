---
title: "GTK+ theme in Kubuntu"
date: 2005-06-28
forum: Desktop Environments
---

### Post by Youssef on 2005-06-28
I've rencently installed Kubuntu, I am satisfied by the results, but I have a problem. GTK+ apps look very ugly . I installed the gtk-qt engine, but it only helped me to make abiword and other gnome apps look better, but apps like amule and xmms still have a very ugly look.

---

### Post by Knome_fan on 2005-06-28
Hi,
xmms and probably your version of amule use gtk1 and as far as I know the gtk-qt-engine doesn't work with gtk1.

However, as a workaround you could use the beep-media-player instead of xmms. It's a workalike but it's written with gtk2, so it should look better.

And there is a newer version of amule in backports. As I don't use it, I don't really know if it is now using gtk2, but you could give it a try.
Take a look at [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories) on how to add backport repositories.

Hope this helps.

---

### Post by Youssef on 2005-06-28
Thanks for the reply, but even if I choose a normal gtk theme like clearlooks or industrial, application like audacity , amule and xmms don't use it .

---

### Post by Knome_fan on 2005-06-28
Yes, because clearlooks is only a gtk2 theme, whereas xmms for example uses gtk1.

---

### Post by Flawed on 2005-06-28
I've found gtk-qt doesn't work right with root applications, either, or is there a workaround?

---

### Post by elsewhere on 2005-06-28
[QUOTE=Flawed]I've found gtk-qt doesn't work right with root applications, either, or is there a workaround?[/QUOTE]

You need to run KControl as root (run *kdesu kcontrol*), then you can set the gtk-qt engine settings there to match the ones you're using for your own profile.

Hope this helps...

Cheers,
KV

---

### Post by Youssef on 2005-06-30
I installed aMule CVS compiled against GTK2, so OK !

---

