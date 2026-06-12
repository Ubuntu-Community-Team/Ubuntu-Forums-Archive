---
title: "adding hotmail to Evolution"
date: 2009-05-26
forum: General Help
---

### Post by newbie09 on 2009-05-26
i followed instruction in setting up hotmail for Evolution ... the link below has the steps ...

[http://ubuntuforums.org/showthread.php?t=200408](http://ubuntuforums.org/showthread.php?t=200408)

now when i reach the step where i enter the following command in the terminal 
[B]
sudo apt-get install hotway hotsmtp[/B]

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hotway

i get the error message above ... 

can anyone tell me how to resolve issue

i checked System -> Software Sources and the following are check marked Open Source (main, universe, restricted & multiverse) ... the Source Code option has a line across the box ... the CD option is not checked since i do not have a cd

i installed Ubuntu 9.04 via the Wubi Windows installer

any ideas???

thanks in advance

---

### Post by Minsky on 2009-05-26
I've had a look at the Hotway page at SourceForge.net, and in the Download section it's referenced as **hotwayd**. Try entering:

```
sudo apt-get install hotwayd hotsmtp
```

Hope that works

---

### Post by newbie09 on 2009-05-28
i finally got it to work thanks due to this link

[http://linuxowns.wordpress.com/2009/03/04/setting-up-evolution-mail-gmail-and-hotmail/](http://linuxowns.wordpress.com/2009/03/04/setting-up-evolution-mail-gmail-and-hotmail/)

if anyone else has any problems

---

### Post by mschraier on 2009-06-05
Hotmail now is a free pop account.

pop server: pop3.live.com
smtp server: smtp.live.com

set pop to listen to port 995 and make sure it is using SSL

set smtp to listen to port 587, amke sure to use SSL and require authentication.

i used it in outlook on XP and kamil in kubuntu

---

