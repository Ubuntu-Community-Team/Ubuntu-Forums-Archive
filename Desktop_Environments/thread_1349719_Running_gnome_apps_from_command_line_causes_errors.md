---
title: "Running gnome apps from command line causes errors"
date: 2009-12-08
forum: Desktop Environments
---

### Post by wyattbiker on 2009-12-08
This is brand new 9.10 32 bit installation. I installed the server followed by full installation of the desktop. Everything works fine except when I run a desktop app (such as gedit or gksudo nautilus) from terminal I get the following error, repeated maybe 20 times:

(nautilus:3672): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

Any ideas why?

---

### Post by SandmanCL on 2009-12-12
No answer, but I came here today looking for a solution to the same problem so I'm replying to this thread in hopes it will receive some attention. What's going on ? I've been running 9.04 w/o problems until i decided to upgrade today (not a fresh install, but upgrading via the package manager) and get that message when I try to launch apps from command line to remove X11 server.

---

### Post by SandmanCL on 2009-12-12
This fixed it for me:
[http://ubuntuforums.org/showpost.php?p=8457206&postcount=3](http://ubuntuforums.org/showpost.php?p=8457206&postcount=3)

```

cd
rm -rf .dbus .gcon* .gnome2 .gnome2_private

```

---

