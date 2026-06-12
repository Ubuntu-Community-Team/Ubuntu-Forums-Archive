---
title: "How do I check a service status"
date: 2005-12-21
forum: Desktop Environments
---

### Post by tuxster on 2005-12-21
I am new to ubuntu and need to know how to check the status of a service, or start and stop a service.  If using Mandrake, a command like "service smb status" would tell me if samba was running or not "service smb restart" would stop and restart the service.  When I try to run it in ubuntu, it says "command not found".  Not sure if it's just a path issue but I also cant find the "service" executable.  Can somebody point me in the right direction ?  Thanks....

Mike

---

### Post by 23meg on 2005-12-21
You can use ps. ```
ps -e |grep smb
```

---

### Post by gnu2tux on 2005-12-21
[QUOTE=tuxster]I am new to ubuntu and need to know how to check the status of a service, or start and stop a service.  If using Mandrake, a command like "service smb status" would tell me if samba was running or not "service smb restart" would stop and restart the service.  When I try to run it in ubuntu, it says "command not found".  Not sure if it's just a path issue but I also cant find the "service" executable.  Can somebody point me in the right direction ?  Thanks....

Mike[/QUOTE]

Hi Mike,

Services that are installed on your system can be found in /etc/init.d, those which are set up to run will be called by the init process. Some processes start from /etc/rcS.d, some from rc1.d and rc2.d.

Most standard services start from rc2.d in ubuntu.

for example, I could stop and start a service like this:

$sudo /etc/init.d/samba stop
$sudo /etc/init.d/samba start

or, simply restart it:

$sudo /etc/init.d/samba restart

many you can check what arguments it takes, simply by leaving the last argument blank, eg:

$sudo /etc/init.d/samba

Hope this helps!

--
For all the information a Linux Newbie Needs to know, visit the Ultimate Linux Newbie Guide! -- Advice on Choosing, Using and Installing Linux as well as a step-by-step guide on installing Ubuntu 5.10

[CENTER]
Visit today!
[http://www.linuxnewbieguide.org]("http://www.linuxnewbieguide.org")[/CENTER]

---

### Post by tuxster on 2005-12-21
Thanks gnu2tux and 23meg.  Thats the second question I've posted on this forum and got good answers to both right away.  I think I'm going to like this forum.  Now, I have one more question, how can I add /etc/init.d/  to my fixed command path ?

---

### Post by 23meg on 2005-12-22
If what you want to do is make it easier to type and remember, instead of doing that, you may want to set bash aliases to certain tasks; for example you can substitute the "ps -e |grep smb" with something like "checksmb" or anything else you want. Check [this]("http://www.linuxcommand.org/wss0020.php#aliases") out.

---

### Post by anil_robo on 2005-12-22
For people who prefer to stay away from terminal windows, you can view currently active services by going to System--> Administration--> Services.

Another useful place is System--> Preferences--> Sessions--> Current Session.

---

