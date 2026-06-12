---
title: "Enemy Territory 2.55"
date: 2008-04-29
forum: Gaming &amp; Leisure
---

### Post by Diefree on 2008-04-29
Hi im new to linux. (must hear that alot)
anyways i have a clan on Wolf Et 2.55 and want to set up a server BUT i keep getting this stupid error when ever i try to install.

/home/david/.setup6503: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
./setup.sh: line 143:  6533 Segmentation fault      "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.1

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting

Now before you tell me to go to 2.60 or 2.60b dont... IM A DIE HARD 2.55 FAN NEVER WILL UPDATE. 

Please help

Sincerly Dave

---

### Post by gerbman on 2008-04-29
What does the output of ```
ls -l /usr/lib | grep libgtk
```look like?

---

### Post by Diefree on 2008-04-29
lrwxrwxrwx  1 root root       21 2008-04-28 14:38 libgtkhtml-2.so.0 -> libgtkhtml-2.so.0.0.0
-rw-r--r--  1 root root   378216 2005-11-15 11:23 libgtkhtml-2.so.0.0.0
lrwxrwxrwx  1 root root       24 2008-04-28 14:38 libgtkhtml-3.8.so.15 -> libgtkhtml-3.8.so.15.3.9
-rw-r--r--  1 root root   621616 2006-08-01 04:17 libgtkhtml-3.8.so.15.3.9
lrwxrwxrwx  1 root root       29 2008-04-28 14:38 libgtksourceview-1.0.so.0 -> libgtksourceview-1.0.so.0.0.0
-rw-r--r--  1 root root   180920 2006-07-31 17:03 libgtksourceview-1.0.so.0.0.0
lrwxrwxrwx  1 root root       20 2008-04-28 14:38 libgtkspell.so.0 -> libgtkspell.so.0.0.0
-rw-r--r--  1 root root    18328 2005-10-24 23:31 libgtkspell.so.0.0.0
lrwxrwxrwx  1 root root       26 2008-04-28 14:38 libgtk-x11-2.0.so.0 -> libgtk-x11-2.0.so.0.800.20
-rw-r--r--  1 root root  2950692 2006-08-02 08:50 libgtk-x11-2.0.so.0.800.20



Wow your fast thx

---

### Post by gerbman on 2008-04-29
> **Diefree said:**
> lrwxrwxrwx  1 root root       21 2008-04-28 14:38 libgtkhtml-2.so.0 -> libgtkhtml-2.so.0.0.0
-rw-r--r--  1 root root   378216 2005-11-15 11:23 libgtkhtml-2.so.0.0.0
lrwxrwxrwx  1 root root       24 2008-04-28 14:38 libgtkhtml-3.8.so.15 -> libgtkhtml-3.8.so.15.3.9
-rw-r--r--  1 root root   621616 2006-08-01 04:17 libgtkhtml-3.8.so.15.3.9
lrwxrwxrwx  1 root root       29 2008-04-28 14:38 libgtksourceview-1.0.so.0 -> libgtksourceview-1.0.so.0.0.0
-rw-r--r--  1 root root   180920 2006-07-31 17:03 libgtksourceview-1.0.so.0.0.0
lrwxrwxrwx  1 root root       20 2008-04-28 14:38 libgtkspell.so.0 -> libgtkspell.so.0.0.0
-rw-r--r--  1 root root    18328 2005-10-24 23:31 libgtkspell.so.0.0.0
lrwxrwxrwx  1 root root       26 2008-04-28 14:38 libgtk-x11-2.0.so.0 -> libgtk-x11-2.0.so.0.800.20
-rw-r--r--  1 root root  2950692 2006-08-02 08:50 libgtk-x11-2.0.so.0.800.20
I don't see any libgtk1.2 references, so try the following:```
sudo apt-get install libgtk1.2
```Try to run the installer after that, and if it still doesn't work post the output of ```
ls -l /usr/lib | grep libgtk
```again.

---

### Post by Diefree on 2008-04-29
OMG i LOVE YOU!!!! you just saved my clan alot of money...

THANK YOU THANK YOU THANK YOU!!!!

---

### Post by gerbman on 2008-04-29
> **Diefree said:**
> OMG i LOVE YOU!!!! you just saved my clan alot of money...

THANK YOU THANK YOU THANK YOU!!!!Haha...well, I do accept donations...  ;)

---

