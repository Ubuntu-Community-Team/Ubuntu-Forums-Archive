---
title: "can't find application"
date: 2005-04-11
forum: Desktop Environments
---

### Post by jkeck55 on 2005-04-11
I used synaptic to download a couple of games (nethack, and tuxpuck)  now I cannot find them.  How do I get them to show up in the menus?  If I can't do that how do I run them?

---

### Post by danip on 2005-04-11
applications>run>tuxpuck

I don't have the other program installed but im sure that it will work the same way.

---

### Post by cwaldbieser on 2005-04-12
Or from the terminal program:

```
$ nethack
```

If you go to the properties tab for the package in synaptic, you can choose to see the list of files installed.  Usually, there will be one or more programs installed in /usr/bin that will be the ones you can run.

If they don't get put on the menu, you can create desktop shortcuts to them, or you could create a folder full of links to them.  There are lots of different ways to keep track of them.

If you go to the terminal and hit TAB twice, you can actually see a list of every executable command in your PATH.  If you type the first couple letters of the command and hit tab, you can see a list of all the commands that start with the letters you typed.

---

