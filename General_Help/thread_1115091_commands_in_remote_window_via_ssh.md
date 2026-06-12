---
title: "commands in remote window via ssh"
date: 2009-04-03
forum: General Help
---

### Post by paldives on 2009-04-03
This may seem like a strange question.
I have managed to open a terminal-window "so it shows on their desktop" on a remote machine via ssh.  I am trying to send that terminal window some commands so the person on the other end can see what I am doing.  Also is it possible to force the window to be maximized.
The commands I used so far are
export DISPLAY=:0
gnome-terminal
but it just open a blank terminal on their screen.
any ideas or help is welcome.

---

### Post by decoherence on 2009-04-03
I haven't done this myself, but a friend used to. He called the program 'snoop' but the closest thing I could find the in the repository is this 'ttysnoop' that looks like it does the same thing. 

Also, his setup was strictly console... no X11 involved. Not sure if it'll work with X11. Might be worth a look anyway.

---

