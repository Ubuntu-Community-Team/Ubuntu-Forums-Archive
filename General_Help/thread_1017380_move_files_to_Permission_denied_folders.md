---
title: "move files to Permission denied folders"
date: 2008-12-21
forum: General Help
---

### Post by nabilalk on 2008-12-21
Hi, I'm trying to move a file from my desktop to the usr/lib/firefox/plugins folder. When I did:

$ mv /home/username/Desktop/libflashplayer.so /usr/lib/firefox/plugins

I received a cannot move....Permission denied error. I can't copy to this folder using the Desktop environment either. How do I gain access to this and folders like it. I assume I have to be a super user. How do I gain this status? Thanks!

Update: Resolved

> [me@linuxbox me]$ sudo some_command
Password:
[me@linuxbox me]$

Permission denied folders accessed via the sudo command. For more info read [guide to Linux commands]("http://www.linuxcommand.org/learning_the_shell.php")

Wow, you guys are fast! Thanks for the help.

-nka

---

### Post by kellemes on 2008-12-21
> **nabilalk said:**
> $ mv /home/username/Desktop/libflashplayer.so /usr/lib/firefox/plugins


sudo mv /home/username/Desktop/libflashplayer.so /usr/lib/firefox/plugins

---

### Post by abhilashm86 on 2008-12-21
in order to become superuser use this,
in terminal type
sudo su


then it'll ask ur password,then ur status is superuser,try now

---

### Post by Jammanuser on 2008-12-21
Or do "gksu nautilus" without the quotes, and it'll open up a file browser as root...from there, you can copy, move, save files as you please! ;)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by nabilalk on 2008-12-21
> **Jammanuser said:**
> Or do "gksu nautilus" without the quotes, and it'll open up a file browser as root...from there, you can copy, move, save files as you please! ;)

Cheers! :popcorn:

-Jam man

:guitar:

Extremely useful shortcut. Thanks!

---

