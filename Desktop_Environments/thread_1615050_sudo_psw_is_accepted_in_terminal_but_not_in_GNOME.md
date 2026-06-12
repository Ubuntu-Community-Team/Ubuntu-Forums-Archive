---
title: "sudo psw is accepted in terminal but not in GNOME"
date: 2010-11-06
forum: Desktop Environments
---

### Post by jjaakkol on 2010-11-06
For example if I run command in terminal: 
sudo startupmanager, my psw is accepted and startup manager is started correctly.

but if I click "System- Administration- Start Manager" GNOME asks 
"Enter the administrator password" and same psw as in terminal is not accepted.

How to fix this?

My account is assign to admin group, checked via System- Administration- Users and Groups

---

### Post by different_guy on 2010-11-06
Hey jjaakkol!

Check this link: [http://ubuntuforums.org/showthread.php?t=2444](http://ubuntuforums.org/showthread.php?t=2444)

It is a bit old, but maybe it will help you.

---

### Post by wojox on 2010-11-06
Looks like root owns start-up manager. Use gksudo from cli.

[Fix Broken Sudo]("http://www.psychocats.net/ubuntu/fixsudo")

---

### Post by jjaakkol on 2010-11-07
> **wojox said:**
> Looks like root owns start-up manager. Use gksudo from cli.

[Fix Broken Sudo]("http://www.psychocats.net/ubuntu/fixsudo")


I checked things mentioned in link. All are like that. But it did not solved this.

I changed root psw and with that I can now "survive". ;)

---

