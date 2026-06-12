---
title: "Issues detecting .iso and cd when trying to install UT-GotY"
date: 2009-06-20
forum: Gaming &amp; Leisure
---

### Post by Noirblanc on 2009-06-20
heya people, i'm having real issues getting ut to work on my jaunty +64. Well i can play through wine, but that ain't the trick, right?!

This is what happens:

```

```
sudo mount -o loop -t iso9660 /wherever/iso/image/is/image.iso /media/iso/
noir@Noir-desktop:~$ chmod +x unreal.tournament_436-multilanguage.goty.run
noir@Noir-desktop:~$ ./unreal.tournament_436-multilanguage.goty.run
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 436-multilanguage.goty Installer....................................................................................

Gtk-WARNING **: Failed to load module "libcanberra-gtk-module.so": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

Gdk-WARNING **: locale not supported by C library

Gtk-WARNING **: invalid cast from (NULL) pointer to `GtkEntry'

Gtk-CRITICAL **: file gtkentry.c: line 534 (gtk_entry_get_text): assertion `entry != NULL' failed.
noir@Noir-desktop:~$ 

so the installer loads, asks for path; i go for the default, enter.

==> Now it's asking for disk 1!

--> gtk2.0 i got, en libcanberra aswell

Can someone please give me a dummies instruction if i got it wrong here. I tried to follow all the goty install instructions listed with no success, well wine works, but i'm not thrilled aboud it. I will apreaciate any help, thx.

---

### Post by Noirblanc on 2009-06-20
it's indeed from a torrent file

---

### Post by Noirblanc on 2009-06-22
....anything i can do with it?

---

### Post by amrypma on 2011-04-09
!bump!

I've been having the same problem. Is this a checksum thing or something?

---

