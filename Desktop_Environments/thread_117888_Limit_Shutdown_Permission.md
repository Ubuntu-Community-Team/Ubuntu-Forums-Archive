---
title: "Limit Shutdown Permission"
date: 2006-01-15
forum: Desktop Environments
---

### Post by akniss on 2006-01-15
Is there a way that I can require sudo priveleges to shutdown my Breezy machine?  I'm using a Ubuntu box as a little print server, and I don't want my roomates shutting the machine down when they're done looking up porn.  Is there a way that I can require a password to shutdown or reboot the machine?  If not, can I at least remove the two options from the menu when one chooses log out from the system menu?  

I've tried searching these forums and googling, but nothing seems to answer the question that I'm after.

Thanks.

---

### Post by Mr_Grieves on 2006-01-15
You may change permissions on what file you like with the chmod command.
Read about it, permissions, groups and users here: [http://www.unixcities.com/howto/index3.html](http://www.unixcities.com/howto/index3.html)

---

### Post by cwaldbieser on 2006-01-15
[QUOTE=akniss]Is there a way that I can require sudo priveleges to shutdown my Breezy machine?  I'm using a Ubuntu box as a little print server, and I don't want my roomates shutting the machine down when they're done looking up porn.  Is there a way that I can require a password to shutdown or reboot the machine?  If not, can I at least remove the two options from the menu when one chooses log out from the system menu?  

I've tried searching these forums and googling, but nothing seems to answer the question that I'm after.

Thanks.[/QUOTE]

Since they could always just pull the plug irrespective of privleges, you should probably just have a pow-wow with them, and failing that, introduce them to your LART.

---

### Post by akniss on 2006-01-15
[QUOTE=Mr_Grieves]You may change permissions on what file you like with the chmod command.
Read about it, permissions, groups and users here: [http://www.unixcities.com/howto/index3.html](http://www.unixcities.com/howto/index3.html)[/QUOTE]

As a Linux newbie, what file should I go looking for to chmod?  I assume there is a shutdown script somewhere that initiates the process?

---

### Post by akniss on 2006-01-15
[QUOTE=cwaldbieser]Since they could always just pull the plug irrespective of privleges, you should probably just have a pow-wow with them, and failing that, introduce them to your LART.[/QUOTE]

I don't think its really out of spite... just a habit as casual Windows users.  And anyway, the only lart I have is a rubber band collection.  You have to get pretty close range to make those work.   ;)

---

### Post by cwaldbieser on 2006-01-15
[QUOTE=akniss]As a Linux newbie, what file should I go looking for to chmod?  I assume there is a shutdown script somewhere that initiates the process?[/QUOTE]
I think you need to change permissions for the reboot and poweroff commands, but I am not 100% sure.

---

### Post by akniss on 2006-01-26
Its not perfect, but here's what I did:
Under system>preferences>sessions there is a checkbox that gives the option to give the user a choice of what to do upon choosing log out.  I unchecked that box, so now as soon as the user chooses logout, he is immediately taken to the gdm login screen.  This a close to what I wanted, and will work for now.

---

