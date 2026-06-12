---
title: "Sudo Dont Work!!!"
date: 2008-05-24
forum: Desktop Environments
---

### Post by Narbie on 2008-05-24
chi is not in the sudoers file. This incident will be reported.

this happens when i try to use sudo in ubuntu 8.04, i searched on the web and i found this:

[http://ubuntuforums.org/showthread.php?t=107940](http://ubuntuforums.org/showthread.php?t=107940)

but the problem is i can get to the root and visudo file, but then when i start to type its doggey characters some times show up when i type some times dont. so i press s 5 times and only comes up once. anywayz i typed in
chi ALL=(ALL) ALL

but then how on earth do i save it!!??? i don't see no instructions or anything. =.=

oh btw it sudo worked before....

---

### Post by hal8000 on 2008-05-24
> **Narbie said:**
> chi is not in the sudoers file. This incident will be reported.

this happens when i try to use sudo in ubuntu 8.04, i searched on the web and i found this:

[http://ubuntuforums.org/showthread.php?t=107940](http://ubuntuforums.org/showthread.php?t=107940)

but the problem is i can get to the root and visudo file, but then when i start to type its doggey characters some times show up when i type some times dont. so i press s 5 times and only comes up once. anywayz i typed in
chi ALL=(ALL) ALL

but then how on earth do i save it!!??? i don't see no instructions or anything. =.=

oh btw it sudo worked before....



As the original post states, adding your name to the sudoers list is a possible security risk as you have the ability to run commands as root user, and hence anyone exploiting your password or account has the same abiliy.

To answer your question, save the file by pressing
Esc
:wq

thats, escape key then :wq   Visudo uses the same syntax as the vi editor.
You may be better trying to find out what caused this error in the first place.

---

### Post by Narbie on 2008-05-25
i have no idea what caused it, i only been installing virtualbox and trying to set up seamless integration with windows

---

### Post by Narbie on 2008-05-25
okay a bit of a problem
Host_Alias HERE=amnesty
User_Alias PRIVILEGED=anu

Cmnd_Alias ADMIN=/usr/bin/apt

PRIVILEGED HERE=ADMIN, NOPASSWD: ADMIN

this is what i suppose to put into the file. the first 3 is easy because there was titles i knew where they go, but the last one i don't know where on earth i should put it...

and after these codes should i still put in 
chi ALL=(ALL) ALL

i edited some of it so sudo works, so now i opened it with pico i took a screenshot:

[http://img152.imageshack.us/img152/8337/screenshotaw1.png](http://img152.imageshack.us/img152/8337/screenshotaw1.png)

where do i put my last line?

---

### Post by aysiu on 2008-05-25
This should help you:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by Narbie on 2008-05-25
> **aysiu said:**
> This should help you:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

okay i typed

adduser chi admin
in root

i not sure if it works now if i try to open up sudoer file it shows a empty file... but sudo works so i just gonna forget it and carry on :P

---

