---
title: "$home/.dmrc wrong permissions"
date: 2006-06-01
forum: Desktop Environments
---

### Post by Aurdal on 2006-06-01
So, I just today decided I'd give Linux a new try and set up ubuntu to dualboot with Win Xp on my AMD Athlon 64™ Computer.

In anycase, after the installation was finished the GNOME GUI promted me for username and password, which I entered. Only to recieve a error message, I'd expect this from windows, but not linux... :p  In any case the message told me that: $home/.dmrc has wrong permissions and that i should be owned by user and be chmodded to 644. Now to be honest, I'm a total newbie as the last time I got so frustrated I just deleted it and enjoyed having more space in Windows.

What I'm trying to say is that I have no idea how to fix this and that I'd appreciate any help I can get.

PS, I get an other message afterwards saying something about the session and me not being logged in... which I'm not. so..


Thanks
-Aurdal

---

### Post by johnc4510 on 2006-06-01
Applications>Accessories>Terminal
Copy and Paste the following:
chmod -R 755 ~/
sudo chmod 644 ~/.dmrc
The second command, the one with sudo in the first position will immediately ask you for your password. Enter it and when it finishes the command you should be returned to a line like the one you started at:example  
johnc@johnc:~$
When it gets to there, type exit and hit enter

---

### Post by Aurdal on 2006-06-01
That'd be great exept for the fact that I can't actuallylog in when using the GUI, I get some error message about a session thingy...

---

### Post by johnc4510 on 2006-06-01
Reboot the computer, at the boot screen choose recovery mode from the menu, this will give you terminal access.

---

### Post by Aurdal on 2006-06-01
Ok, so tried that... the irst error message is gone, but I still cant log in...
Something about ~.xsession-errors-file

---

### Post by johnc4510 on 2006-06-01
Okay, go back to boot, where you got the terminal and type this:
sudo gedit /home/.xsession-error
enter your password
This should open that file. It should show what the error is. Try to post what it says here.

---

### Post by Aurdal on 2006-06-01
Not that I'm an expertbut I think gedit requires a GUI...

Bleh, I think I'll give a shot at reinstalling it...

---

