---
title: "nautilus, can't open it as root"
date: 2008-11-17
forum: Desktop Environments
---

### Post by ngine13 on 2008-11-17
Hello.

I try to open nautilus as root but nautilus opens for user.

I get the following on the root terminal :

(nautilus:7869): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

---

### Post by Big_Croc7 on 2008-11-17
Try 'gksu nautilus' from a non-root terminal

---

### Post by ngine13 on 2008-11-17
The problem is that when i give 

nautilus

in a root terminal, i get nautilus opened for normal user..

and i also get the warning i wrote to the first post.

Does anyone know why?

---

### Post by ngine13 on 2008-11-17
> **Big_Croc7 said:**
> Try 'gksu nautilus' from a non-root terminal

Thank you for your answer. :)

This one works, but i don't understand why giving the command

nautilus

in a root terminal does not open nautilus for user root..

---

### Post by madverb on 2008-11-17
I think it's something to do with root not being able to find an instance of xserver start as root...
Don't quote me on that though

---

