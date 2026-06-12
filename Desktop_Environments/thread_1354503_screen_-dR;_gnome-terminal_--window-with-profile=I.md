---
title: "screen -dR; gnome-terminal --window-with-profile=Irssi"
date: 2009-12-13
forum: Desktop Environments
---

### Post by laeg_ on 2009-12-13
The command that is the title of this post doesn't seem to work: 

```
screen -dR; gnome-terminal --window-with-profile=Irssi
```

Nor will it work wit && in place of ;.

Basically I want to attach/run screen and irssi from my *Applications* menu with the same launcher regardless of whether screen is running already because I started it remotely using ssh.

I had this setup in 9.04 but I lost the command in the upgrade.

---

### Post by laeg_ on 2009-12-14
```
screen -AadRRS irssi irssi
``` 

This will attach to the irssi screen session if it's already running, if not it will create it.

What it won't do is:

```
gnome-terminal --window-with-profile=Irssi
```

How can I integrate this into the command?

---

### Post by laeg_ on 2009-12-14
SOLVED:

the launcher in my applications menu is just: 

```
gnome-terminal --window-with-profile=Irssi
```

I've set gnome-terminal to execute the command:

```
screen -AadRRS Irssi irssi 
```

And also the default is set *When command exits: Exit the terminal* so when I run it a second time it closes off the last terminal tidily.

---

