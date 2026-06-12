---
title: "Remote Apps using the X system"
date: 2005-07-21
forum: Desktop Environments
---

### Post by schulermx on 2005-07-21
I'm not sure if that's an appropriate title but I will try to describe what I want.

When I'm using my work computer (FC2) or the computers in the school's computer lab (RH9) and I SSH to my files, I can use the X11 when I open files. Example: When I open a file using emacs on the remote server, an emacs window will actually open on my computer. When I do the same thing on my home computer (Ubuntu 5.04) I only get text-mode emacs in the terminal. I would like to have it so an emacs window (or any other program [gedit,gnuplot etc]) will open when I open files on the remote server. 

I hope what I want is clear. Thanks in advance.

---

### Post by cwaldbieser on 2005-07-21
When you ssh to your home computer, you need to turn X forwarding on with the -X switch.  Then if you run an X app on the remote computer, it will be displayed on your local X Server.

---

### Post by schulermx on 2005-07-22
[QUOTE=cwaldbieser]When you ssh to your home computer, you need to turn X forwarding on with the -X switch.  Then if you run an X app on the remote computer, it will be displayed on your local X Server.[/QUOTE]

Well that was extremely simple. Exactly what I was looking for, thanks!

---

### Post by lol on 2005-07-22
[QUOTE=][/QUOTE]
 Also take a look at the files /etc/ssh/ssh_config and /etc/ssh/sshd_config, you can permanently turn on X11Forwarding there...

---

