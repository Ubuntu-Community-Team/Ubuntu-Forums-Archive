---
title: "Application removed but updates keep coming!"
date: 2009-03-29
forum: General Help
---

### Post by danjah on 2009-03-29
Hello all 0/

Okay, I've posted a long time ago about this issue but had no reply.

I've removed items such as cups, bluez and palmos.

I have the problem now that when I want to update ubuntu 8.10 the update list includes all sorts of stuff for cups, and worst of all stuff for Nvidia... Why is this? I use an ATI graphics card and I don't have a printer!
How do i stop recieving updates for stuff I no longer need or use.

DR :popcorn:

---

### Post by sdennie on 2009-03-29
How did you remove the packages?  My initial guess is that they are actually still installed.  Try a few command lines like:

```

dpkg -l | grep -i nvidia
dpkg -l | grep -i bluez
dpkg -l | grep -i cups

```

---

### Post by danjah on 2009-03-30
Thank you for your reply, could you help me further to understand these commands.

If these commands actually remove the packages from the OS, what is the symantic package manager actually doing when I use it to remove applications and device support?

---

### Post by sdennie on 2009-03-30
Doing "dpkg -l" just lists all the packages installed on your machine.  The "| grep -i whatever" is just means only print things that have that word in them (case insensitive).

---

### Post by danjah on 2009-03-30
> **sdennie said:**
> Doing "dpkg -l" just lists all the packages installed on your machine.  The "| grep -i whatever" is just means only print things that have that word in them (case insensitive).

So which part of the command removes the packages from the OS? as this is all I wish to achieve.

---

### Post by sdennie on 2009-03-30
No part.  It's better to diagnose the problem than just blindly try to fix it.  I'm asking for information so I can tell you how to fix it.

---

### Post by Vaphell on 2009-03-30
he wants to diagnose problem, that's why he asks for input of commands showing all package entries with these keywords :-) If you give the answer you'll get precise instructions

---

### Post by danjah on 2009-03-30
> **Vaphell said:**
> he wants to diagnose problem, that's why he asks for input of commands showing all package entries with these keywords :-) If you give the answer you'll get precise instructions

Ahh, well that i do understand! 

Will post a reply when I get home. Thank you.

:popcorn:

---

### Post by danjah on 2009-03-31
> **sdennie said:**
> How did you remove the packages?  My initial guess is that they are actually still installed.  Try a few command lines like:

```

dpkg -l | grep -i nvidia
dpkg -l | grep -i bluez
dpkg -l | grep -i cups

```

$ dpkg -l | grep -i nvidia

$ dpkg -l | grep -i cups
ii  libcups2                                   1.3.9-2                                 Common UNIX Printing System(tm) - libs
ii  libcupsimage2                              1.3.9-2                                 Common UNIX Printing System(tm) - image libs
ii  libgnomecups1.0-1                          0.2.3-2build1                           GNOME library for CUPS interaction

$ dpkg -l | grep -i bluez
ii  libbluetooth3                              4.12-0ubuntu5                           Library to use the BlueZ Linux Bluetooth sta

---

### Post by Vaphell on 2009-03-31
I checked these commands and i get much more results.
It seems these are the shared libraries used by the stuff you uninstalled. Package manager found updates for these leftovers, that's all.
You can uninstall them - find them by name in synaptic and mark to remove. It should do the trick

---

### Post by linuxuser21 on 2009-03-31
Another way that you could possibly do it is: Go System> Administration> Software Sources and then deselect the ones that you want to get rid of.  It'll be more than likely in Third-Party Updates.

---

