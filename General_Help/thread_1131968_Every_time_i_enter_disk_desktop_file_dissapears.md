---
title: "Every time i enter disk desktop file dissapears"
date: 2009-04-21
forum: General Help
---

### Post by broken bot on 2009-04-21
Everytime i enter a blank disk or disk into my cdr driver to try and make a copy all my files lock up and wont let me open them.

i am running jaunty jackalope server.

was trying to make a copy of the desktop version for my laptop but it seems impossible with this error or this file locking.

Thanks in advance.

---

### Post by codeseer on 2009-04-21
Have you tried it with Brasero?

It's under Applications->Sound & Video->Brasero Disc Burner in Intrepid Ibex... probably the same in Jaunty.

If not, you should be able to open a terminal (Applications->Accessories->Terminal) and type 'brasero' and hit Enter to get it. Alternatively, you could hit ALT+F2 and type brasero.

---

### Post by broken bot on 2009-04-21
what appears when i do what you just suggested

```

GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

(brasero:6765): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(brasero:6765): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Segmentation fault

```

---

### Post by codeseer on 2009-04-21
I'm not sure what that is, but it looks like pretty bad trouble.

Did you power off the machine without shutting down at any point?

---

### Post by cariboo on 2009-04-21
Can you copy your home folder to the server and burn it that way? If you are trying to do what I think you are, you need something like [webCDWriter]("http://oerghaeger.de/webCDwriter/").

Jim

---

### Post by broken bot on 2009-04-22
no i was trying to make a copy of jaunty 9.04 desktop because i have server running on my dell (by accident thought was desktop) and was trying to get desktop on a disk to put on my laptop....

---

