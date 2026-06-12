---
title: "Need help to execute ssh daemon"
date: 2009-03-27
forum: General Help
---

### Post by SanZoR on 2009-03-27
Hello,
I got a dedicated server, which i can only access via web panel (ssh daemon didnt started at all). So, my question is, how i can create a pair of scripts, which does start the ftp daemon with user root (sudo -i normally).
The user i can access to it is www-data, and if somebody could give me a script wich does do:
sudo santtu <password>
and executes the ssh daemon.
I would be very thankful!
Thanks in advance, SanZoR

---

### Post by hyper_ch on 2009-03-27
by default openssh-server is not being installed, you need to install it and then you can access the machine by ssh.

---

### Post by albandy on 2009-03-27
www-data don't have sudo privilegies so you can't.

---

### Post by SanZoR on 2009-03-27
> **albandy said:**
> www-data don't have sudo privilegies so you can't.

yeah, but umm...
Can it do "su santtu" ? (santtu is my account on it)
then type the password automatically.
So, then /etc/init.d/sshd start
is this any way possible? :l

---

### Post by albandy on 2009-03-27
so your idea it's to use a php script to do it?
Usually system instructions are disabled by try this:

<?php
echo "<pre>";
system('ls', $stat);
echo "</pre>";
?>

if works you can execute commands throught php

---

### Post by SanZoR on 2009-03-27
> **albandy said:**
> so your idea it's to use a php script to do it?
Usually system instructions are disabled by try this:

<?php
echo "<pre>";
system('ls', $stat);
echo "</pre>";
?>

if works you can execute commands throught php

Okay, now this a bit hard to explain, but i'll try...
I provide game hosting on my server, and the hosting panel is still accessable. the file which i execute in order to start the gameserver is like ./server1, which www-data will do when i press the button in the web panel. Is it possible to modify this game server execution script to start the ssh daemon instead?
I think it is possible, but i dont know how to do it.
Thats why i am asking help in here :P
Anyway, if somebody knows how to fix this, i can pay 5 euro by paypal for the guy who solves this problem.
Thanks in advance, SanZoR

---

### Post by SanZoR on 2009-03-27
-bump-
Anyone? :(

---

