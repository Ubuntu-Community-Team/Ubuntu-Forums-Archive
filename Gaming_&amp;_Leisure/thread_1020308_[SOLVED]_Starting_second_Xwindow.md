---
title: "[SOLVED] Starting second Xwindow"
date: 2008-12-24
forum: Gaming &amp; Leisure
---

### Post by Omecron on 2008-12-24
Forgive me if I said that wrong. I am playing Vendetta Online and liking it a lot. However I cant Alt-Tab out of it to my desktop and it was suggested I should start a second X for Vendetta and switch between like F1 and my normal. I am fine with that, however I don't know how.

Can someone tell me or post a link I can read? I would be very grateful.


Omecron

---

### Post by jpkotta on 2008-12-24
Go to a console with Ctrl-Alt-F1 and log in.  Then```
startx /path/to/vendetta -- :1
```
startx won't run a command unless it is an absolute path, so you need to know where Vendetta Online's launch script/binary is.  If you know the command to start it (let's say it's vendetta-online),```
which vendetta-online
```  Now you can switch between X servers with Ctrl-Alt-F7 and Ctrl-Alt-F8.

---

### Post by thegnark on 2008-12-24
[LIST=1]
[*]Switch to tty1 (Ctrl-Alt-F1)
[*]Run this command
```
startx -- :1
```
[*]To return to your original X session, switch to tty7 (Ctrl-Alt-F7)
[*]To return to your new X session, switch to tty8 (Ctrl-Alt-F8 )
[*]To end your new X session, simply logout as normal, and switch back to tty7  (Ctrl-Alt-F7)
[/LIST]
Source: [http://www.hermann-uwe.de/tips-and-tricks/multiple-x11-sessions](http://www.hermann-uwe.de/tips-and-tricks/multiple-x11-sessions)

You may also want to consider playing with xnest to embed one X session within another:
Source: [http://www.debian-administration.org/articles/80](http://www.debian-administration.org/articles/80)

I haven't personally tried xnest, but it might be worth a shot.

Hope that helps! :)

---

### Post by Omecron on 2008-12-24
Thanks a bunch! Appreciate it  :)

---

### Post by jpkotta on 2008-12-24
> **thegnark said:**
> [LIST=1]
[*]Switch to tty1 (Ctrl-Alt-F1)
[*]Run this command
```
startx -- :1
```
[*]To return to your original X session, switch to tty7 (Ctrl-Alt-F7)
[*]To return to your new X session, switch to tty8 (Ctrl-Alt-F8 )
[*]To end your new X session, simply logout as normal, and switch back to tty7  (Ctrl-Alt-F7)
[/LIST]
Source: [http://www.hermann-uwe.de/tips-and-tricks/multiple-x11-sessions](http://www.hermann-uwe.de/tips-and-tricks/multiple-x11-sessions)

You may also want to consider playing with xnest to embed one X session within another:
Source: [http://www.debian-administration.org/articles/80](http://www.debian-administration.org/articles/80)

I haven't personally tried xnest, but it might be worth a shot.

Hope that helps! :)

Xephyr is a better replacement for Xnest.

---

