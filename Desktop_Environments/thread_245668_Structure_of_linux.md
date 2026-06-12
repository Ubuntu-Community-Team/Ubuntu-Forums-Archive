---
title: "Structure of linux"
date: 2006-08-28
forum: Desktop Environments
---

### Post by asmith3006 on 2006-08-28
Hi.
Is there a nice picture that explains the structure of linux? I'm very confused with things like xserver and the kernal and gnome and so on. There seems to be millions of layers that you can change and I have no idea what the different bits do. Would be great if there was a tree type diagram showing the functions and names of the bits.

Cheers.
Andrew.

EDIT: Argh, posted in the wrong forum. This should be in absolute beginners sorry :(

---

### Post by peabody on 2006-08-28
```

[FONT="Courier New"]
--------------------
|Gnome User Intrfc |
--------------------
|Gnome Libraries   |
--------------------
|GUI libraries(gtk)|
--------------------
| X11 System (xorg)|
--------------------
| Unix Land (CLI)  |
--------------------
| libc, syscalls   |
--------------------
| Linux Kernel     |
--------------------
[/FONT]

```

That's a simplest way I know how to put it.  Anything in depth would be staring at the sun.  You definitely want to take one step at a time.  Slowly.  Get comfortable with the GUI.  Then learn some of the command line.  Maybe finally learn a thing or two about the Linux filesystem.

---

### Post by fhj on 2006-08-28
You can also check out the Linux FAQ at
[http://www.tldp.org/FAQ/Linux-FAQ/index.html](http://www.tldp.org/FAQ/Linux-FAQ/index.html)

- fhj

---

### Post by tkjacobsen on 2006-08-28
Found this on google picture search: [http://www.codemartial.org/Linux/images/KernelStructure.gif](http://www.codemartial.org/Linux/images/KernelStructure.gif)

This is mostly the kernel

---

