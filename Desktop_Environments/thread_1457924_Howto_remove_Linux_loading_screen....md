---
title: "Howto remove Linux loading screen... ?"
date: 2010-04-19
forum: Desktop Environments
---

### Post by stoynev on 2010-04-19
Hello, I would like to remove the linux loading screen, right after the system boots from the boot loader (grub) to be black blank until it loads!?

How can I do that.

---

### Post by micio on 2010-04-19
Set NOSPLASH switch in grub.cfg (or menu.lst) in your kernel line.

It should work :P

---

### Post by stoynev on 2010-04-20
SOLVED , thanks :)

---

### Post by infamous-online on 2010-04-20
Wow, something I didn't know about and I've been using Ubuntu forever over here, thanks for the tip.

---

### Post by Iowan on 2010-04-20
> **stoynev said:**
> SOLVED , thanks :)

[SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by d3v1150m471c on 2010-04-20
```

gksudo nautilus /usr/local/share/images

```

Create a backup of these images and then make alterations to them in gimp to customize a login screen as opposed to canning it if you like.

---

### Post by stoynev on 2010-04-21
[B]In Ubuntu 8.x its via usplash , you can download Splash Screens from gnome-look.org > Splash Screens 

In Ubuntu 9.x is the same but at some point it goes to another stage of splash booting which is > Xsplash , in order to change that you need to go to /usr/share/images/xsplash and you will see the images ....

Thats all...[/B] :)

---

