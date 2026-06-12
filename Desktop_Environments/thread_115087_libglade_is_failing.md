---
title: "libglade is failing"
date: 2006-01-09
forum: Desktop Environments
---

### Post by Jairo Marin on 2006-01-09
Hello comunity, this is my first post here. :smile: 
 
 I'm asking for help because I have days with this problem and I don't know what else to do...  ](*,) 

 When I try to run gdmsetup I get :

gdmsetup: symbol lookup error: /usr/lib/libglade-2.0.so.0: undefined symbol: gtk_about_dialog_get_type

and the same with synaptic:

synaptic: symbol lookup error: /usr/lib/libglade-2.0.so.0: undefined symbol: gtk_about_dialog_get_type

I am using Xubuntu Breezy Badger 5.10. (Xfce)   :-({|= 

I tried reinstalling libglade.2-0, synaptic and gdm with aptitude but I still get the same error.

I don't know if this help, but knew I do " $ ls -l /usr/lib/libglade* " it returns:

-rw-r--r-- 1 root root 96192 2005-07-08 10:12 /usr/lib/libglade-2.0.a
-rw-r--r-- 1 root root 1218 2005-07-08 10:12 /usr/lib/libglade-2.0.la
lrwxrwxrwx 1 root root 21 2006-01-07 22:28 /usr/lib/libglade-2.0.so -> libglade-2.0.so.0.0.7
lrwxrwxrwx 1 root root 21 2006-01-08 18:16 /usr/lib/libglade-2.0.so.0 -> libglade-2.0.so.0.0.7
-rw-r--r-- 1 root root 86520 2005-07-08 10:12 /usr/lib/libglade-2.0.so.0.0.7
-rw-r--r-- 1 root root 103128 2004-08-13 04:14 /usr/lib/libglade.a
-rw-r--r-- 1 root root 3386 2004-08-13 04:14 /usr/lib/libglade-bonobo.a
-rw-r--r-- 1 root root 1589 2004-08-13 04:14 /usr/lib/libglade-bonobo.la
lrwxrwxrwx 1 root root 24 2006-01-08 18:09 /usr/lib/libglade-bonobo.so -> libglade-bonobo.so.0.4.2
lrwxrwxrwx 1 root root 24 2006-01-08 18:09 /usr/lib/libglade-bonobo.so.0 -> libglade-bonobo.so.0.4.2
-rw-r--r-- 1 root root 6464 2004-08-13 04:14 /usr/lib/libglade-bonobo.so.0.4.2
-rw-r--r-- 1 root root 441 2004-08-13 04:14 /usr/lib/libgladeConf.sh
-rw-r--r-- 1 root root 51854 2004-08-13 04:14 /usr/lib/libglade-gnome.a
-rw-r--r-- 1 root root 1406 2004-08-13 04:14 /usr/lib/libglade-gnome.la
lrwxrwxrwx 1 root root 23 2006-01-08 18:09 /usr/lib/libglade-gnome.so -> libglade-gnome.so.0.4.2
lrwxrwxrwx 1 root root 23 2006-01-08 18:09 /usr/lib/libglade-gnome.so.0 -> libglade-gnome.so.0.4.2
-rw-r--r-- 1 root root 57072 2004-08-13 04:14 /usr/lib/libglade-gnome.so.0.4.2
-rw-r--r-- 1 root root 879 2004-08-13 04:14 /usr/lib/libglade.la
-rw-r--r-- 1 root root 54258 2005-08-26 19:00 /usr/lib/libglademm-2.0.a
-rw-r--r-- 1 root root 1926 2005-08-26 19:00 /usr/lib/libglademm-2.0.la
lrwxrwxrwx 1 root root 23 2006-01-08 18:09 /usr/lib/libglademm-2.0.so -> libglademm-2.0.so.1.0.6
lrwxrwxrwx 1 root root 23 2006-01-08 18:09 /usr/lib/libglademm-2.0.so.1 -> libglademm-2.0.so.1.0.6
-rw-r--r-- 1 root root 37680 2005-08-26 19:00 /usr/lib/libglademm-2.0.so.1.0.6
-rw-r--r-- 1 root root 1898 2005-09-07 05:41 /usr/lib/libglademm-2.4.la
lrwxrwxrwx 1 root root 23 2006-01-08 08:34 /usr/lib/libglademm-2.4.so -> libglademm-2.4.so.1.0.4
lrwxrwxrwx 1 root root 23 2006-01-08 08:34 /usr/lib/libglademm-2.4.so.1 -> libglademm-2.4.so.1.0.4
-rw-r--r-- 1 root root 39736 2005-09-07 05:41 /usr/lib/libglademm-2.4.so.1.0.4
lrwxrwxrwx 1 root root 17 2006-01-08 18:09 /usr/lib/libglade.so -> libglade.so.0.4.2
lrwxrwxrwx 1 root root 17 2006-01-08 18:09 /usr/lib/libglade.so.0 -> libglade.so.0.4.2
-rw-r--r-- 1 root root 94096 2004-08-13 04:14 /usr/lib/libglade.so.0.4.2

If you need more information to help me , please tell me what is it and I'll post it ... [-o< 
Thanks ...

---

