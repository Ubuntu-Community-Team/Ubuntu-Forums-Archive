---
title: "wireless problem in Ubuntu9.04"
date: 2009-06-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pravindra.kumar on 2009-06-06
Dear,
I have Dell Vostro A840 laptop and i installed Ubuntu9.04 Desktop, in this version Wireless LAN is not working but Wired is working, i am very new to this OS so i do not understand that what to do.
Please help me.

Thanks !!!!!!!!!!

---

### Post by coffeeaddict22 on 2009-06-06
Hi,
 Welcome to Linux!  
First up, it's easiest to use a terminal.  Look in Applications/Accessories and there's a terminal in there; I copy it to my top panel (right click it for the option) because it's useful.  The main reason is that it's a ton easier to explain what to type than which button to push; output is also way more explicit when trying to get to the bottom of a problem.

Any command in the terminal will have a page of info on it in a man page; for instance, lshw is a command that stands for list hardware.  type " man lshw" in a terminal, and you'll get more info than you currently want.  Use the man pages; there's all sorts of gems in there.

With wireless, there's a few commands to identify the problem.  Type them in a terminal, then cut and paste the output back here, and we'll help.  So try the following, paste it back, and we'll go from there.
```
lshw -C network
iwconfig
nm-tool
```

---

### Post by kiridude on 2009-06-07
If you left click your wireless icon in the panel, is "wireless" and "networking" enabled?

---

### Post by billyfd on 2009-06-07
You can always try, System>Administration>Hardware Drivers and search for driver, and if there is one referring to your wireless card, then activate it.

---

### Post by Crickwilson on 2009-06-08
I have this same problem on my friends hp I had set up for dual boot, I'd like to see if this works.

---

