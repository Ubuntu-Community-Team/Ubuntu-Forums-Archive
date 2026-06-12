---
title: "Run command in terminal from menu item"
date: 2008-07-22
forum: Desktop Environments
---

### Post by madm0nk on 2008-07-22
I am trying to add an item to the gnome menu which opens up a terminal and runs a command then when it finishes to run a command prompt. The best I could get is a terminal that opens, runs the command, then closes (I can set the terminal to stay open in the profile setting but it is useless).


i.e. Edit Menus->New Item, Type: Application in terminal Name: Python Command: python

this will open a terminal displaying the python prompt accordingly, now when you hit ctrl-d the terminal becomes useless.

---

### Post by QwUo173Hy on 2008-07-22
Use whatever name you like, but make the command:
> gnome-terminal -e python

---

### Post by madm0nk on 2008-07-22
> **jarlath said:**
> Use whatever name you like, but make the command:

That just opens up a terminal as a child process. i.e. you get 2 terms one running python which still becomes useless after hitting ctrl-d, and the other is useless from the start.

---

### Post by QwUo173Hy on 2008-07-23
Ctrl-d always closes the terminal does it not? I mean, regardless of how you launch the terminal, ctrl-d will kill it. Even with xterm.

But the command I gave you only launches 1 terminal.

---

### Post by madm0nk on 2008-07-23
> **jarlath said:**
> Ctrl-d always closes the terminal does it not? I mean, regardless of how you launch the terminal, ctrl-d will kill it. Even with xterm.

But the command I gave you only launches 1 terminal.

ctrl-d sends a signal to the current process which python handles as quit. Normally I believe it kills the stdin (which would make a terminal useless if you hit it at the prompt).

try running nmap instead of python (may have been a bad example) and you will see what I am talking about.

Edit: Ok hitting ctrl-d at the prompt does kill the term either way running gnome-terminal -e python (or any other command) doesn't work.

---

