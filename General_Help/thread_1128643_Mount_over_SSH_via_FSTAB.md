---
title: "Mount over SSH via FSTAB"
date: 2009-04-17
forum: General Help
---

### Post by MetalMusicAddict on 2009-04-17
So I've seen the HOWTOs on mounting over SSH but there's something I'm missing when I want to use it in a FSTAB. Which currently looks like: [SIZE="1"](obviously edited for privacy)
[/SIZE]
```
sshfs#user@42.42.42.42:/media/Storage /media/Storage fuse defaults 0 0
```

So I wanna mount from my home server (is there anything I need to install there?) to a client on the outside.

I need to go out of town and this would be killer to get working. Also, I'd like to automount without needing to input a password.

Any tips?

---

### Post by phinullfermata on 2009-04-17
There is a way to do that with autofs.  There's a tutorial in the tutorials and tips section on it, just search something like "ssh autofs".  I use it for myself, and it works great, although takes a little bit to get configured perfect.

---

### Post by MetalMusicAddict on 2009-04-17
> **phinullfermata said:**
> There is a way to do that with autofs.  There's a tutorial in the tutorials and tips section on it, just search something like "ssh autofs".  I use it for myself, and it works great, although takes a little bit to get configured perfect.
Thanx. I'll look into it.

---

