---
title: "proftpd problemos"
date: 2009-05-21
forum: General Help
---

### Post by GnubbyaBush on 2009-05-21
Hey so i've finally finished configuring my proftpd.config file to my liking, and i attached it. For some reason i'm getting the dreaded 503 error on connect (using FlashFxp). I've got the port (1980) forwarded on my router and everything actually connects but then theres a login issue at the password. I've got the password and username correct though. So i erased the user "userftp" and tried to recreate it, well now it says userftp is already been created. Is there any code where i can officially erase userftp so i can recreate it? As for the 503 error i created another user "userftp1" and changed my config file accordingly so that I could try again, still no luck with the 503 error. I saw some people saying to do sudo passwd userftp1, and retype the password. This still didn't work (and i stopped the server and started it again between the password change).

Also i tried to enable the tsl/ssh encyrption i found in this tut [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588), i ran all the commands but ran into troubles with the "sudo openssl req -new -x509 -days 365 -key ca.key -out ca.ct" command. It said it couldn't create the key becasue something was missing in the config file. Also i had similar <if modules> already in the config file, i started to think i was reiterating info already there and screwing everthing up so i took out the code.

---

