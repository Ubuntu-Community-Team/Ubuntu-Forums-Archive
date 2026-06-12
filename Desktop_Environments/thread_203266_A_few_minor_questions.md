---
title: "A few minor questions"
date: 2006-06-24
forum: Desktop Environments
---

### Post by Blazeix on 2006-06-24
Hi, I'm using 6.06 with fluxbox. I have two (hopefully easy) questions. My first is about starting the xscreensaver daemon on startup. Currently I have to start xscreensaver manually in order for it to load the daemon. I have "xscreensaver &" in my "/etc/X11/xinit/xinitrc" file, but it still doesn't seem to work. Am I doing something wrong?

My second question is about the shutdown command. Currently on my system, when I type "shutdown -r now" it notifies me that I have to be root in order to shutdown my system. Is there some way to shutdown my computer without being root? It is somewhat of a pain to have to enter my password everytime I want to shutdown. Thanks!

---

### Post by adwait on 2006-06-25
For the first try [http://ubuntuforums.org/showthread.php?t=78425&highlight=running+startup](http://ubuntuforums.org/showthread.php?t=78425&highlight=running+startup)

It has instructions about how to make a command run on startup.

For your second question, why not shutdown from the GUI? Why do you need to use the CLI??

---

### Post by Blazeix on 2006-06-25
Thanks for the link, that fixed my xscreensaver problem.
As for shutting down, I'm using fluxbox as my window manager. It doesn't have a shutdown button. I try to do most of my stuff through the command line anyway, just so I can learn more about linux and not depend on a gui. I was thinking I could play around with the sudoers file, but I'm really not sure how to do that.

---

### Post by ayoli on 2006-06-25
Using sudo visudo edit the following file: /etc/sudoers and add this line
```
USERNAME ALL = NOPASSWD: /sbin/shutdown
```
do not forget to replace 'USERNAME' with your user name.
regards.

---

