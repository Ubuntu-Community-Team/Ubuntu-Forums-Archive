---
title: "nautilus as root"
date: 2009-04-18
forum: General Help
---

### Post by dharmagio on 2009-04-18
hi
i am trying to run nautilus as root with the command "gksu nautilus" or "gksudo nautilus" the nautilus window starts with errors...

(nautilus:20009): Eel-WARNING **: GConf error: 
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

then i try to cut paste some files i want to put in audacious skin folder but it does not work, i do cut but then i cant do paste in the folder i want, any help ?

---

### Post by ronparent on 2009-04-18
Simply runing [/B]sudo nautilus[/B] has always worked for me!

---

### Post by alan.m.howard on 2009-04-18
Can't say that I can help you with the Nautilus error, but if you just need root privileges to move some files then you could do it from the terminal using

sudo mv file_to_be_moved new_location

Just a thought.

---

### Post by dcstar on 2009-04-18
```
gksudo "dbus-launch nautilus --no-desktop --browser %U
```

---

### Post by dharmagio on 2009-04-19
thanks

sudo nautilus, worked for me too

moving a lot of files in the terminal its just pain
and this way it just works with little effort

---

### Post by dcstar on 2009-04-20
> **dcstar said:**
> ```
gksudo "dbus-launch nautilus --no-desktop --browser %U
```

This is the only way that you retain full Nautilus functionality (network browsing etc), plain sudo/gksudo loses things.

---

### Post by qwertymodo on 2009-04-20
Thanks dcstar, I often had weird errors showing up with gksudo nautilus but I ignored them cus it seemed to work regardless.  Guess I never tried any of the "things that got lost"... care to elaborate on what exactly those things are?  It always did bug me...

---

