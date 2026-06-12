---
title: "Not so portable hard drive"
date: 2009-04-30
forum: General Help
---

### Post by Bearded-flower on 2009-04-30
Is it possible to "plug" this old hard drive we have lying it around into my laptop to make a external hard drive of sorts?

---

### Post by Grenage on 2009-04-30
Indeed, what you'll need is an external drive chassis; they're pretty cheap.  Basically a box with an IDE/SATA to USB adapter and a power input.

Edit: WTF with your signature.

---

### Post by Bearded-flower on 2009-04-30
OH no. like its an actual computer not just the hard drive.
i know u can get an adapter for just the hard drive.
But i mean the computer as a whole.
sorry my fault i should have given more detail

---

### Post by Grenage on 2009-04-30
So you could connect to it across a network cable, and mount the share?

---

### Post by Bearded-flower on 2009-04-30
Ok im using ubuntu (intrepid) and the computer is using XP and its an oooooooooooooooold hp
how do i do that?

---

### Post by Bearded-flower on 2009-04-30
*COUGH COUGH*
Oh sorry about that
any ideas

---

### Post by Paqman on 2009-04-30
> **Bearded-flower said:**
> OH no. like its an actual computer not just the hard drive.
i know u can get an adapter for just the hard drive.
But i mean the computer as a whole.
sorry my fault i should have given more detail

If you've got a router, just plug into that and browse to the machine through Nautilus. If you want to plug it directly into your machine you'll need a crossover ethernet cable. Either way you're just networking the two machines together. 

It would be way simpler (and certainly a lot more power-efficient) to just pull out the hard drive from the old machine and put it into a drive caddy like Grenage suggested.

---

### Post by Grenage on 2009-04-30
Here's how you'd do it for a one-off:

[http://www.cyberciti.biz/tips/how-to-mount-remote-windows-partition-windows-share-under-linux.html](http://www.cyberciti.biz/tips/how-to-mount-remote-windows-partition-windows-share-under-linux.html)

Here's how you'd do it so that it mounts when you boot up ubuntu (windows machine needs to be on):

[http://industriousone.com/mounting-windows-shares-linux](http://industriousone.com/mounting-windows-shares-linux)

Like Paqman says, it's ideal to put the drive in the nix machine, but if you want to keep them separate, I'd opt for a script shortcut that mounts the share on demand.

---

### Post by Bearded-flower on 2009-05-10
Oh, i only need to do it once.
Im only usin it to dump all my files onto it of my laptop im then going to install jaunty over the whole thing (including windows partition and then retrieve the files

---

