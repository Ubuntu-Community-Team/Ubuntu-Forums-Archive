---
title: "Logitech G15 LCD+G key support help"
date: 2006-09-20
forum: Desktop Environments
---

### Post by &lt;StAiNlEsS&gt; on 2006-09-20
hey guys, this is my first post.
i've had ubuntu installed for about 4 days now. i've managed to get all my hardware to work except my Logitech G15 keyboard.

I used Synaptic to download G15lcd and G15Display but i cannot get anything to happen on my keyboard

atm Ubuntu sees the keyboard as a defult 104 key keyboard.

this is a copy of the terminal I tried to run G15LCD and G15Display.

NAME@NAME:~$ sudo /etc/init.d/g15lcd start
Password:
Starting g15lcd...
g15lcd already started.
NAME@NAME:~$ g15display
sh: /var/run/g15lcd: Permission denied
NAME@NAME:~$ 

any help would be greatly appricated.
cheers.

---

### Post by &lt;StAiNlEsS&gt; on 2006-09-20
bump.

---

### Post by Zay on 2006-09-21
**sudo** g15display?

---

### Post by T-Chip on 2006-09-26
You can check out this thread for some quick answers:
[http://www.ubuntuforums.org/showthread.php?t=108542]("http://www.ubuntuforums.org/showthread.php?t=108542")

If you can't find any answers there, get back to this thread :-)

---

### Post by Aneurysm9 on 2006-09-28
You can try the new generation of g15lcd at [http://g15tools.sf.net/](http://g15tools.sf.net/)  I don't have .debs available, but I'm working on it.

---

### Post by drdnl on 2006-09-28
I've made a howto: explaining the installation of the G15Tools plus some debs here [http://www.ubuntuforums.org/showthread.php?t=267118]("http://www.ubuntuforums.org/showthread.php?t=267118")

---

