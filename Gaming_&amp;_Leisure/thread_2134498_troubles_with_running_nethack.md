---
title: "troubles with running nethack"
date: 2013-04-11
forum: Gaming &amp; Leisure
---

### Post by MadleSs on 2013-04-11
Hi guys... When I'm trying to run nethack with ./nethack I get this message:
```
Unknown terminal type: xterm.
```
Can anyone help? Thanks :)

---

### Post by Perfect Storm on 2013-04-11
Try running nethack with xterm instead through gnome-terminal instead (You can find xterm in Dash).
See if the game runs there.

Also which nethack packages did you installed?

---

### Post by MadleSs on 2013-04-11
I have downloaded nethack package from official site ... And my problem is solved ... I used this:

[LIST]
[*]sudo apt-get install ncurses-term 

[*]sudo ln -s /lib/terminfo/x/xterm /usr/share/terminfo/x/xterm
It works now 


[/LIST]

---

### Post by Perfect Storm on 2013-04-11
Great!
I'll mark your thread solved ^_^

---

