---
title: "Help! I hosed X!"
date: 2005-05-08
forum: Desktop Environments
---

### Post by benplaut on 2005-05-08
i think i messed something up.

i was following some instructions of how to improve the performance of ATI Mobile 7500, and i was tinkering with my xorg.conf file. Of course, i made a backup of the file, but it doesn't help.

when i booted, it announced that an error had occured, and asked me if i wanted to see the log. the log was also corrupt, so it took me to a CLI login. i logged in and proceded to restore my backup:

$ sudo cp -i /home/ben/xorg.conf /etc/X11/xorg.conf
(typed y, then enter)

i tried startx, but it announced:

X: cannot stat /etc/X11/X (Nosuch file or directory), aborting.

so i rebooted....













and nothing changed.
Another weird thing is that Hoary LiveCD can't find or mount hda1...  ](*,)

---

### Post by kvidell on 2005-05-08
[QUOTE=benplaut]i think i messed something up.

i was following some instructions of how to improve the performance of ATI Mobile 7500, and i was tinkering with my xorg.conf file. Of course, i made a backup of the file, but it doesn't help.

when i booted, it announced that an error had occured, and asked me if i wanted to see the log. the log was also corrupt, so it took me to a CLI login. i logged in and proceded to restore my backup:

$ sudo cp -i /home/ben/xorg.conf /etc/X11/xorg.conf
(typed y, then enter)

i tried startx, but it announced:

X: cannot stat /etc/X11/X (Nosuch file or directory), aborting.[/QUOTE]
from /etc/X11/xorg.conf:
 ```
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg
```

Give that a shot maybe?
Be sure to keep that original of yours in your $HOME handy.
- Kev

Also:
is /usr/bin/X11/Xorg happy? (Permissions and existance)

---

### Post by benplaut on 2005-05-08
how do i check permissions from CLI?

---

### Post by kvidell on 2005-05-08
[QUOTE=benplaut]how do i check permissions from CLI?[/QUOTE]
 ```
ls -ldh /path/to/file
```
- Kev

---

### Post by benplaut on 2005-05-08
OK, semi-solved-

i did the ^^ to create a new xorg.conf, and now i have a working T40 with...

GUI!!!  \\:D/ 

and now, off to the task of getting middle-scroll to work  :roll:

---

