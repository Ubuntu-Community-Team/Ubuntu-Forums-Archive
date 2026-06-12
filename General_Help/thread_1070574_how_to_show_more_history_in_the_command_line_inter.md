---
title: "how to show more history in the command line interface"
date: 2009-02-15
forum: General Help
---

### Post by philidox on 2009-02-15
How do you show history in the command line.  For example when I type **ls** in the /usr/bin file it shows a lot of programs but I hit **SHIFT+PageUp** and it will only allow me to go up so far in the list.  How do I remedy this issue.

---

### Post by x33a on 2009-02-15
you can pipe the output to less

try "ls | less"

---

### Post by geirha on 2009-02-15
You can also increase the number of lines the terminal will remember. If you are using gnome-terminal, go to Edit -> Active Profile -> Scrolling(tab).

---

### Post by zacktu on 2009-02-15
Two other ways to view history:
[LIST]
[*]Use the up and down arrows in the command line.
[*]Use the "history" command.  I just checked, and I can see from 73 to 572, so I guess that the default is 500.
[/LIST]

---

### Post by scooper on 2009-02-15
If you're on a text console, e.g. by typing Ctrl-Alt-F1, I don't know a way to increase the buffering.  That doesn't mean there isn't a way.  I think you get more available to Shift-PgUp if you don't use the framebuffer for your text console.  You'd have to tweak the kernel command line options and probably sacrifice the pretty start up display.

If it's an X terminal, like gnome-terminal or konsole, then there's a simple configuration option to control how many lines are saved.  E.g. for gnome-terminal it's on the Scrolling tab of Profile Preferences.  I set mine to 9999 lines.  Konsole lets you choose "unlimited".

---

