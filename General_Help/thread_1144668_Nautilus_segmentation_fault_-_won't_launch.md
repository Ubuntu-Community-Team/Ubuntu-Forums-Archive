---
title: "Nautilus segmentation fault - won't launch"
date: 2009-04-30
forum: General Help
---

### Post by ricardisimo on 2009-04-30
:~$ nautilus
/usr/share/themes/Peace/gtk-2.0/gtkrc:55: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/usr/share/themes/Peace/gtk-2.0/gtkrc:56: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/Peace/gtk-2.0/gtkrc:57: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
Segmentation fault

---

### Post by kanikilu on 2009-04-30
I'm not sure if the segfault is related to the warnings you are getting about your theme, but, it would appear that you are using an old theme that uses some features that are no longer supported. You might want to try temporarily switching to another theme to see if the problem with nautilus remains...

---

### Post by ricardisimo on 2009-05-01
No, I switched to the default Ubuntu Human theme, and I still get the seg fault, just no warnings about clearlooks. I think some Xubuntu users are having the same issue. Ironically, i have to say "Thank you thunar", otherwise I'd have no file browser.

Any ideas on how to fix this?

---

### Post by narcisgarcia on 2009-05-02
May be it related to his bug?

[https://bugs.launchpad.net/ubuntu/+bug/355970](https://bugs.launchpad.net/ubuntu/+bug/355970)

---

### Post by geirha on 2009-05-02
If you create a new user and try to start nautilus with that user, do you also get a segfault?

---

### Post by possid on 2009-05-03
If nautilus only crashes on certain folders, the problem could be situated in a file (or all files with a certain extension). You could try to copy all files in your home folder to another, temporary folder and locate the problem by deleting the files in this temporary folder one by one.

I had the same kind of error after changing my /usr/share/mime/packages/freedesktop.org.xml file (I made it incorrect obviously).

---

### Post by afrodeity on 2010-05-27
bump

---

