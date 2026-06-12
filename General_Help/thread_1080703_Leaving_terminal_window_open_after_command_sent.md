---
title: "Leaving terminal window open after command sent"
date: 2009-02-25
forum: General Help
---

### Post by Fastjack77 on 2009-02-25
Hi everyone,

Under Gnome, I've created a launcher with the following command "route -n; read". My goal is to be able to simply look at the route tables without having to open the terminal, write the command and press enter. Instead, I want a window to open (terminal) and show me the resulting data.

Using "route -n; read" appears to work, but as soon as the command is sent, the window closes. I tried using piped commands, such as less, more, and read, to no avail.

How can I launch any command to the terminal without having the window closing after execution?

Thanks in advance! :KS

---

### Post by caljohnsmith on 2009-02-25
Instead of using the "run in terminal" option, try this as the command:
```
gnome-terminal -x bash -c "route -n;read -n1"
```
Then when you press any key, the terminal should close. Let me know if that's what you are looking for or not.

---

### Post by Fastjack77 on 2009-02-25
Hi caljohnsmith,

This is it! It works perfectly. I think I'm at a point where I have to start learning bash.

You rock! =D>

Thanks,

Fastjack

---

### Post by caljohnsmith on 2009-02-25
Glad that's what you were looking for; cheers and have fun learning more bash commands. :)

---

