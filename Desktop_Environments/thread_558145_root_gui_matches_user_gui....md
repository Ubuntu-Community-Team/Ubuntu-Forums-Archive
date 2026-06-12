---
title: "root gui matches user gui..."
date: 2007-09-23
forum: Desktop Environments
---

### Post by c_olin on 2007-09-23
I'm a picky kind of guy.  I noticed that the gnome theme when running a program as root is different than running a program as a regular user.  How can i change the gnome theme of the root user?

---

### Post by yabbadabbadont on 2007-09-23
This should give you an idea of how it is done.  :D
```
/home/daffy $ sudo -i
Password:
/root # ls -la
total 40
drwxr-xr-x   4 root root 4096 2007-09-23 14:43 .
drwxr-xr-x  28 root root 4096 2007-09-18 22:25 ..
drwx------   2 root root 4096 2007-09-23 14:01 .aptitude
-rw-r--r--   1 root root    6 2007-09-18 21:01 .bash_logout
-rw-r--r--   1 root root 1548 2007-09-18 21:02 .bashrc
lrwxrwxrwx   1 root root   18 2007-09-18 22:30 .fonts -> /home/daffy/.fonts
lrwxrwxrwx   1 root root   18 2007-09-18 22:30 .gtkrc -> /home/daffy/.gtkrc
lrwxrwxrwx   1 root root   22 2007-09-18 22:30 .gtkrc-1.2 -> /home/daffy/.gtkrc-1.2
lrwxrwxrwx   1 root root   22 2007-09-18 22:30 .gtkrc-2.0 -> /home/daffy/.gtkrc-2.0
lrwxrwxrwx   1 root root   18 2007-09-18 22:29 .icons -> /home/daffy/.icons
-rw-r--r--   1 root root  209 2007-09-18 21:02 .profile
-rw-------   1 root root 1024 2007-09-19 17:33 .rnd
lrwxrwxrwx   1 root root   19 2007-09-18 22:30 .themes -> /home/daffy/.themes
-rw-------   1 root root 5062 2007-09-23 14:43 .viminfo

```
Basically, create symbolic links to the .fonts, .icons, .themes directories in your normal user's home as well as to the .gtkrc-1.2 file.  I have .gtkrc and .gtkrc-2.0 because I don't use Gnome normally.  You probably won't have those files, so don't worry about them.

---

### Post by c_olin on 2007-09-23
That worked beautifully, thanks.  I thought of copying the files from my home folder... but this way is much more elegant.

---

