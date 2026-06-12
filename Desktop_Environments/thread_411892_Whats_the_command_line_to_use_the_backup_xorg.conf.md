---
title: "Whats the command line to use the backup xorg.conf?"
date: 2007-04-17
forum: Desktop Environments
---

### Post by elchato on 2007-04-17
...went down again... help please?

I have 2 backups 

```

/etc/x11/xorg.conf.backup 
```

and

```

/root/xorg.conf.backup 
```


when I do 
```

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf 
``` 

it tells me that one of the files does no exist... wich is false.
any help please? THANKS!

---

### Post by Swab on 2007-04-17
You must be making a mistake.  Keep in mind that file names are case sensitive.

---

### Post by elchato on 2007-04-17
*cries inconsolably*

NOOO!!

---

### Post by Swab on 2007-04-17
OK, do this..
```

cd /etc/X11
ls -la

```

Paste the result back here.

---

### Post by elchato on 2007-04-17
```

ubuntu@ubuntu:~$ cd /etc/x11
bash: cd: /etc/x11: No such file or directory

```

It seems to me I can access /etc but not /etc/x11. I can see it in my file browser though. Remember Im using the livecd right now.

EDIT... for some reason It just worked

```
 total 27
drwxr-xr-x  10 root root    80 2007-04-17 17:49 .
drwxr-xr-x 121 root root  2040 2007-04-17 17:57 ..
drwxr-xr-x   2 root root   536 2007-03-22 07:30 app-defaults
drwxr-xr-x   2 root root    87 2007-03-22 07:30 cursors
-rw-r--r--   1 root root    14 2007-03-22 07:31 default-display-manager
drwxr-xr-x   6 root root    52 2007-03-22 07:24 fonts
lrwxrwxrwx   1 root root     6 2007-03-22 07:23 gdm -> ../gdm
-rw-r--r--   1 root root 17371 2007-02-13 10:02 rgb.txt
lrwxrwxrwx   1 root root    13 2007-03-22 07:30 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root    69 2007-03-22 07:25 xinit
drwxr-xr-x   2 root root   243 2007-03-22 07:22 xkb
-rw-r--r--   1 root root  3586 2007-04-17 17:49 xorg.conf
drwxr-xr-x   2 root root    27 2007-03-22 07:21 Xresources
drwxr-xr-x   2 root root    31 2007-03-22 07:30 xserver
-rwxr-xr-x   1 root root  3911 2006-08-07 19:01 Xsession
drwxr-xr-x   2 root root   206 2007-03-22 07:31 Xsession.d
-rw-r--r--   1 root root   234 2006-08-07 19:01 Xsession.options
-rw-------   1 root root   614 2007-03-22 07:21 Xwrapper.config

```

cant see me xorg.conf.backup there

---

### Post by Swab on 2007-04-17
the directory is /etc/X11 and not /etc/x11

---

### Post by elchato on 2007-04-17
bahhhh... my first day with ubuntu has been all ups and downs...
dont want to go back to windows!

---

### Post by elchato on 2007-04-17
IT WORKS!!!

YAY! Thanks

uh... but beryl is not working
ill re-install it

---

### Post by elchato on 2007-04-17
ok... still it wont work

---

### Post by elchato on 2007-04-17
ok... UP AND RUNNING!

THANKS A LOT!

---

