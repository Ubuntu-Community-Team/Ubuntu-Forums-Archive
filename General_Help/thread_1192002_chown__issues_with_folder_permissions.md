---
title: "chown  issues with folder permissions"
date: 2009-06-19
forum: General Help
---

### Post by luigi94 on 2009-06-19
i installed true combat elite and to avoid certain issues i have to change the folders permissions by writing in terminal these 2 commands:

-_sudo chown -vRf username:group /usr/local/games_

and this works fine

_-sudo chown -vRf username:group /home/.etwolf/_

but this doesn't work and i get this output:
[I]chown: cannot access '/home/.etwolf' : no such file or directory
failed to change ownership of '/home/.etwolf/' to luigi

[/I]i had to hand write everything because epiphany wont let me copy in this thing so even if 
i tiped something in wrong it is not the problem .
can someone please help???!!!

i use ubuntu 8.10 64-bit

---

### Post by michy99 on 2009-06-19
It should probably be /home/YOURUSERNAME/.etwolf/

---

### Post by luigi94 on 2009-06-19
yes i now i just wrote it down wrong

---

### Post by luigi94 on 2009-06-19
but i still can't figure out why it wont work

---

### Post by michy99 on 2009-06-19
From your home directory, what is the output of```
ls -la
```

---

### Post by luigi94 on 2009-06-19
luigi@luigi-laptop:~$ ls -la
total 604
drwxr-xr-x 32 luigi luigi   4096 2009-06-19 21:03 .
drwxr-xr-x  3 root  root    4096 2009-06-19 09:43 ..
drwx------  3 luigi luigi   4096 2009-06-19 16:01 .adobe
-rw-------  1 luigi luigi   2522 2009-06-19 21:42 .bash_history
-rw-r--r--  1 luigi luigi    220 2009-06-19 09:43 .bash_logout
-rw-r--r--  1 luigi luigi   3115 2009-06-19 09:43 .bashrc
drwxr-xr-x  3 luigi luigi   4096 2009-06-19 14:12 .cache
drwx------  3 luigi luigi   4096 2009-06-19 15:56 .compiz
drwxr-xr-x  6 luigi luigi   4096 2009-06-19 18:35 .config
drwx------  3 luigi luigi   4096 2009-06-19 14:12 .dbus
-rw-------  1 luigi luigi     28 2009-06-19 18:53 .dmrc
drwxr-xr-x  2 luigi luigi   4096 2009-06-19 14:12 Documenti
-rw-------  1 luigi luigi     16 2009-06-19 14:12 .esd_auth
drwxr-xr-x  5 luigi luigi   4096 2009-06-19 20:44 .etwolf
lrwxrwxrwx  1 luigi luigi     26 2009-06-19 09:43 Examples -> /usr/share/example-content
drwxr-xr-x  2 luigi luigi   4096 2009-06-19 18:58 .fontconfig
drwx------  4 luigi luigi   4096 2009-06-19 18:54 .gconf
drwx------  2 luigi luigi   4096 2009-06-19 22:05 .gconfd
-rw-r-----  1 luigi luigi      0 2009-06-19 19:37 .gksu.lock
drwx------ 10 luigi luigi   4096 2009-06-19 20:06 .gnome2
drwx------  2 luigi luigi   4096 2009-06-19 14:12 .gnome2_private
drwx------  2 luigi luigi   4096 2009-06-19 14:12 .gnupg
drwxr-xr-x  2 luigi luigi   4096 2009-06-19 17:34 .gstreamer-0.10
-rw-r--r--  1 luigi luigi    108 2009-06-19 19:17 .gtk-bookmarks
dr-x------  2 luigi luigi      0 2009-06-19 18:54 .gvfs
-rw-------  1 luigi luigi   1881 2009-06-19 18:54 .ICEauthority
drwx------  2 luigi luigi   4096 2009-06-19 16:00 .icedteaplugin
drwxr-xr-x  2 luigi luigi   4096 2009-06-19 14:12 Immagini
-rw-r--r--  1 luigi luigi 230454 2009-06-19 17:20 jhkj.bmp
drwx------  3 luigi luigi   4096 2009-06-19 14:12 .local
drwx------  3 luigi luigi   4096 2009-06-19 16:01 .macromedia
drwxr-xr-x  2 luigi luigi   4096 2009-06-19 14:12 Modelli
drwx------  4 luigi luigi   4096 2009-06-19 14:20 .mozilla
drwxr-xr-x  2 luigi luigi   4096 2009-06-19 14:12 Musica
drwxr-xr-x  3 luigi luigi   4096 2009-06-19 18:49 .nautilus
-rw-r--r--  1 luigi luigi    675 2009-06-19 09:43 .profile
drwxr-xr-x  2 luigi luigi   4096 2009-06-19 14:12 Pubblici
drwxr-xr-x  2 luigi luigi   4096 2009-06-19 14:12 .pulse
-rw-------  1 luigi luigi    256 2009-06-19 14:12 .pulse-cookie
-rw-------  1 luigi luigi   3312 2009-06-19 21:03 .recently-used.xbel
drwxr-xr-x  3 luigi luigi   4096 2009-06-19 21:47 Scrivania
-rw-r--r--  1 luigi luigi      0 2009-06-19 14:13 .sudo_as_admin_successful
drwx------  3 luigi luigi   4096 2009-06-19 17:21 .thumbnails
drwxr-xr-x  2 luigi luigi   4096 2009-06-19 15:46 .update-manager-core
drwx------  2 luigi luigi   4096 2009-06-19 14:14 .update-notifier
drwxr-xr-x  2 luigi luigi   4096 2009-06-19 14:12 Video
-rw-r--r--  1 luigi luigi 160140 2009-06-19 18:37 wicd_1.5.1_all3.deb
-rw-------  1 luigi luigi    123 2009-06-19 18:53 .Xauthority
-rw-r--r--  1 luigi luigi  39422 2009-06-19 22:04 .xsession-errors
luigi@luigi-laptop:~$

---

### Post by luigi94 on 2009-06-19
could it maybe be because the folder is invisibile?

---

### Post by merlinus on 2009-06-19
```

gksu nautilus

```

Navigate to the folder, right-click, select properties and then permissions.

---

### Post by bodhi.zazen on 2009-06-19
> **luigi94 said:**
> could it maybe be because the folder is invisibile?

no, it is because the path is wrong.

The full path is 

/home/luigi/.etwolf

and not 

/home/.etwolf/

You can use ~ or $HOME if you wish

~ is short hand for /home/username and $HOME is a (bash) environmental variable.

```
sudo chown -vRf username:group ~/.etwolf
```

---

### Post by luigi94 on 2009-06-19
thanks

---

