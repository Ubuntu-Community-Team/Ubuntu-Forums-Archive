---
title: "How do I &quot;DisallowTCP=false&quot; in KDE?"
date: 2005-12-11
forum: General Help
---

### Post by mr.dad on 2005-12-11
I have installed ubuntu recently on two of my old PCs which are both connected to my home network. I loaded one with GNOME and the other with KDE.  

When I tried displaying xterm windows from remote machines, I recieved the error mesage "**xterm Xt error: Can't open display"**.  I added "ALL: 192.168.1.*" to the /etc/hosts.allow file on both machines. That did not work. A little site searching enlightended me that I needed edit the file /etc/gdm/gdm.conf and change the DisallowTCP=true to false. This is doable on the GNOME machine and solved the problem for my GNOME machine.  How do I do the equivilant on the KDE box?  

Thanks, Dave

---

### Post by mlomker on 2005-12-12
Hmm.  I've only had to issue the xhost command (must be executed by the logged-in user, not sudo).

```

xhost +

```

---

### Post by Zaventh on 2005-12-12
are you using ssh or telnet? Make sure and use the -X flag from the ssh client to enable x11 forwarding.

---

### Post by mlomker on 2005-12-12
I found it.  You need to do this in addition to xhost.  Edit the /etc/kde3/kdm/kdmrc file and comment out this line:

```

# This string is subject to word splitting.
# Default is ""
#ServerArgsLocal=-nolisten tcp

```

You have to restart KDE for it to take effect.

---

### Post by TheOrangeRider on 2007-05-30
thanks! it was taking me forever trying to figure out why i couldn't connect to my x server

---

