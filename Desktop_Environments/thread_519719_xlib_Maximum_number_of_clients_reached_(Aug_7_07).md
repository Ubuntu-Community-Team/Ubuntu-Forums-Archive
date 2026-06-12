---
title: "xlib Maximum number of clients reached (Aug 7 07)"
date: 2007-08-07
forum: Desktop Environments
---

### Post by supradave on 2007-08-07
I recently tried to upgrade to KDE 4 beta (announced last week).  I don't know what happened, but now I get the message Xlib: Maximum number of clients reached.  I have tried the xlsclient and I get a list of things that are running.  I did the xwininfo -root -children and let it run every 10 seconds over the night.  I have removed the KDE 4 upgrades.  When I went to bed, it was around 370 and when I woke up, it was about 480.  So, something is not too happy.

BTW, this also happens in Gnome, i.e. the Xlib error.

In looking at things, like lsof, I find that I have 400+ instances of something like the following: 
init          1       root  cwd   unknown                                /proc/1/cwd (readlink: Permission denied)
init          1       root  rtd   unknown                                /proc/1/root (readlink: Permission denied)
init          1       root  txt   unknown                                /proc/1/exe (readlink: Permission denied)
init          1       root NOFD                                          /proc/1/fd (opendir: Permission denied)
ksoftirqd     2       root  cwd   unknown                                /proc/2/cwd (readlink: Permission denied)
ksoftirqd     2       root  rtd   unknown                                /proc/2/root (readlink: Permission denied)
ksoftirqd     2       root  txt   unknown                                /proc/2/exe (readlink: Permission denied)
ksoftirqd     2       root NOFD                                          /proc/2/fd (opendir: Permission denied)
watchdog/     3       root  cwd   unknown                                /proc/3/cwd (readlink: Permission denied)
watchdog/     3       root  rtd   unknown                                /proc/3/root (readlink: Permission denied)
watchdog/     3       root  txt   unknown                                /proc/3/exe (readlink: Permission denied)
watchdog/     3       root NOFD                                          /proc/3/fd (opendir: Permission denied)

Which leads to:
ls -1 /proc/1
lrwxrwxrwx   1 root root 0 2007-08-07 08:43 cwd -> /
lrwxrwxrwx   1 root root 0 2007-08-07 07:30 exe
dr-x------   2 root root 0 2007-08-07 08:43 fd
lrwxrwxrwx   1 root root 0 2007-08-07 08:43 root -> /

Which lead to:
file /proc/1/exe
exe: unreadable symlink `exe' (No such file or directory)

Another strange thing I have observed, particularly when running x11vnc and viewing my 0:0 desktop remotely, is that the screensaver kicks in frequently.  But then I went and looked at ps -ef without out running x11vnc and the screensaver (kdesktop_lock) was running.  I killed it and it came back up.  It doesn't show up on my regular desktop, so I don't know where it's running at.

I guess my question is, how do I fix the Maximum number of clients reached problem.  I understand that I'm probably barking up the wrong tree with the proc, but I cannot figure out what's wrong.

---

