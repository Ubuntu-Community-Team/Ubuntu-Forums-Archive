---
title: "Installation problems"
date: 2005-04-20
forum: Desktop Environments
---

### Post by saint_geser on 2005-04-20
Yesterday I installed Ubuntu Linux 5.04 and a problem occured during the installation. During the installation I was never asked tp type superuser password, so, after the installation is complete I can not use root privileges! If anyone knows what to do, please help!

---

### Post by heimo on 2005-04-20
Hi!
 
This must be the most asked question around here. :) But I'm celebrating my 200th message and thus instead of referencing FAQs, I'll just tell you that it's normal. It's the way Ubuntu is configured by default.
 
You can use sudo to run commands as root and if you insist using root the way it's done in many other distributions, you can use sudo to run passwd to change roots password. Command is sudo passwd root.
 
Welcome to forums and Ubuntu.
 
PS. Password sudo is asking is the one you gave to the first normal user account.

---

### Post by saint_geser on 2005-04-20
Wow \\:D/ ! It works! But why couldn't they do it as it is done in other distributions? 

Thanks!

---

### Post by heimo on 2005-04-20
[QUOTE=saint_geser]Wow \\:D/ ! It works! But why couldn't they do it as it is done in other distributions? 
[/QUOTE]
 
My theory is that it has something to do with Ubuntus desire to get more traffic on their discussion forums. Without that decision on this forum would be only couple dozen members. ;) I think the root password / sudo peculiarity was also the reason I originally came here and got addicted in this user support role.

---

### Post by kvdnberg on 2005-04-20
[QUOTE=saint_geser]Wow \\:D/ ! It works! But why couldn't they do it as it is done in other distributions? 

Thanks![/QUOTE]

Some of the reasons are explained here:

[http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

---

### Post by senorian on 2005-04-20
Thanks for the link to the "sudo" page.
[http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)
However the initial guides:
"sudo passwd root"
"sudo passwd -l root"

Have no semicolon. wheras the subsequent ones do:
"A good workaround is to enable the root account before dealing with the affected packages (sudo su-; passwd <password>) and to lock it again afterwards (su -; passwd -l). "
Being a complete newbie I thought the presence or absence of a semicolon (or any punctuation) was critical?
thanks

---

