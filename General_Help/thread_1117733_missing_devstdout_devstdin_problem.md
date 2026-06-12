---
title: "missing /dev/stdout /dev/stdin problem"
date: 2009-04-06
forum: General Help
---

### Post by Keith Hedger on 2009-04-06
Got a bit of an odd problem, I have been using videotrans to make dvds of home movies which worked fine in Gutsy, but after upgrading to Hardy, some of the scripts and the generated xml file for dvdauthor, have failed as they reference /dev/stdin and /dev/stdout neither of which seem to be in the /dev folder on Hardy but are in Gutsy, I did a work around by copying the files from a gutsy install ( a rescue partition ), but for future reference I would like to know how to create these files properly.
I'm fine with the command-line so be as techinical as you like.
No rush on this problem but I would like to know how to do it.
Thanks!

---

### Post by Keith Hedger on 2009-04-06
Anyone?

---

### Post by ajt on 2009-12-05
> **Keith Hedger said:**
> Got a bit of an odd problem, I have been using videotrans to make dvds of home movies which worked fine in Gutsy, but after upgrading to Hardy, some of the scripts and the generated xml file for dvdauthor, have failed as they reference /dev/stdin and /dev/stdout neither of which seem to be in the /dev folder on Hardy but are in Gutsy, I did a work around by copying the files from a gutsy install ( a rescue partition ), but for future reference I would like to know how to create these files properly.
I'm fine with the command-line so be as techinical as you like.
No rush on this problem but I would like to know how to do it.
Thanks!

Hello, Keith.

I've just noticed the same problem in Dapper (6.06 LTS), and it's caused by a bug in /dev/MAKEDEV, which interprets "fd" as a request to create the "floppy" devices instead of the "fd" file descriptor devices. Here's a patch to fix the problem:
```

 diff -Naur old/MAKEDEV.200511251516 MAKEDEV
--- old/MAKEDEV.200511251516    2005-11-25 15:16:52.000000000 +0000
+++ MAKEDEV     2009-12-05 18:21:14.000000000 +0000
@@ -254,7 +254,7 @@
                        st)     echo st0 ;;
                        xd)     echo xda xdb ;;
                        ad)     echo ada adb ;;
-                       fd)     echo fd0 fd1 ;;
+                       floppy) echo fd0 fd1 ;;
                        lp)     echo lp ;;
                        mt)     echo ftape ;;
                        qft)    echo ftape ;;

```

After applying the patch, create the devices like this:
```

cd /dev
sudo ./MAKEDEV fd

```

Bye,

  Tony.

---

