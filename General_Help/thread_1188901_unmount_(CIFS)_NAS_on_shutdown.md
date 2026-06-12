---
title: "unmount (CIFS) NAS on shutdown?"
date: 2009-06-16
forum: General Help
---

### Post by mailman1175 on 2009-06-16
I've added an entry to /etc/fstab to automagically mount my NAS (external hard drive, mounted to a windows XP machine) to a local directory on start up.

```
# Entry for automounting network attached storage locally
//192.168.2.5/MyBook /home/jeff/MyBook cifs
fmask=0777,dmask=0777,auto,sync 0 0
```

Works like a charm. On shutdown, though, I often get an error message -- something to the effect of

```
CIFS server not responding
```

and it fails to unmount the share. I had the same problems with Fedora 10, and I suspect it spun off into some other difficulties I was having. Is there an entry I can add somewhere (similar to what I did with fstab) that will forcibly unmount the share during the shutdown routine?

---

### Post by callan79 on 2009-06-16
> **mailman1175 said:**
> I've added an entry to /etc/fstab to automagically mount my NAS (external hard drive, mounted to a windows XP machine) to a local directory on start up.

```
CIFS server not responding
```




Hi mailman1175,

I have the same problem on many, many machines that I look after.

Basically the reason is that in GNOME default state, your network is controlled by the NetworkManager applet. So the second you exit GNOME, you lose your network connection.

Of course no network connection = can't talk to the NAS = can't unmount it properly = error messages.

It's never caused me any drama, I just ignore it.

From what I hear, if you get rid of networkmanager and configure your network manually, this solves the problem.

Good luck!

Callan

---

