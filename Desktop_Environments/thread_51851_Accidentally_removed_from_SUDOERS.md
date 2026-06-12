---
title: "Accidentally removed from SUDOERS"
date: 2005-07-25
forum: Desktop Environments
---

### Post by PARAPA on 2005-07-25
Hi,
I have one user account which I accidentally removed from the sudoers group. This now means I am unable to perform any root tasks.

Can anyone offer any assistance in this please?

---

### Post by angkor on 2005-07-25
Read this thread to be able to add yourself back to the sudoers list.

[http://ubuntuforums.org/showthread.php?t=33084](http://ubuntuforums.org/showthread.php?t=33084)

Edit: Assuming you don't have a root account enabled. :)

---

### Post by aggiechemist on 2005-07-25
I assume you still can get into root.

I would log in as root through the terminal (press ctrl alt F1 to get to terminal). Then run "visudo".

At the bottom of the file that comes up there should be a line that looks like

root ALL=(ALL) ALL or something like that.

Just add a line after that that is 

username ALL=(ALL) ALL where you put in the username you need. You should be all fixed up. This occasionally happens in Ubuntu, I've never figured out why. If you can't get into root, post again and I might have a fix for that as well.

---

### Post by PARAPA on 2005-07-25
Hi thanks, 
Im unable to get into root :(

---

### Post by angkor on 2005-07-25
Then just read the thread I mentioned and use the install cd in recovery mode

---

### Post by majikstreet on 2005-07-25
[QUOTE=angkor]Then just read the thread I mentioned and use the install cd in recovery mode[/QUOTE]
 You don't need to use the install cd, it's automagically in the grub boot menu. Read my post in that thread.

---

