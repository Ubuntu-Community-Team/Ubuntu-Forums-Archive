---
title: "Cups user problem"
date: 2006-09-06
forum: Desktop Environments
---

### Post by cybermatthieu on 2006-09-06
Hi,
I'm just trying to install my printer in cups. I get to the add printer wizard with my browser at 127.0.0.1:631/. At the end of the wizard when I click on add printer I get a prompt asking me for a username password. I then put in root and he's password but the prompt just pops up again and again. I tested the root password (I had to put one) in bash with no problem.

I'm I missing something?:-k 

Thanks,
Matt

---

### Post by useResa on 2006-09-06
Hi,  I have the same problem as you have, but searching the forum I came across the following thread [http://www.ubuntuforums.org/showthread.php?t=246323](http://www.ubuntuforums.org/showthread.php?t=246323).    
I think it is quite clearly explained in this thread, but since I am currently not behind my Linux machine (occasionally I do have to pretend I am working 8) ) I can not test it.
Maybe this will help you (and me) getting past this prompt.
Kind regards and good luck

---

### Post by tomBorgia on 2006-09-06
I absolutely hate the web printer config... its a proper pain in the a$$ to get the username / password to work - I've read a simple solution from somewhere on here - try in a terminal

sudo apt-get install gnome-cups-manager

then run sudo gnome-cups-manager (works with xubuntu... havent tried kubuntu)

u should get a "proper" gui printer manager which actually works... :-D

---

### Post by jis on 2006-09-06
If you do not want to install gnome-cups-manager, check
[http://www.ubuntuforums.org/showthread.php?p=1469714](http://www.ubuntuforums.org/showthread.php?p=1469714)
(also my post there)

---

