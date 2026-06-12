---
title: "webmin doesn't work out of LAN"
date: 2006-09-12
forum: Desktop Environments
---

### Post by Lualah on 2006-09-12
if i connect to webmin from LAN then works, if i try to connect out of LAN then connection is refused. I search in webmin configuration that i will disable this but i didin't find anythig. Where can i change this?

EDIT: forgot to foward port

---

### Post by SlowYaRoll on 2006-09-19
There's another thread out there that'll probably help you with your webmin tasks.

Check out this thread:
[http://www.ubuntuforums.org/showthread.php?t=195093&page=4]("http://www.ubuntuforums.org/showthread.php?t=195093&page=4") 


In addition, here's the info that applies to your specific problem.

[INDENT]Login to webmin, go to WEBMIN CONFIGURATION, then go to IP ACCESS CONTROL and select Allow from all addresses, then hit save. That should do the trick for you.

or

From the command line, 
sudo nano /etc/webmin/miniserv.conf
Find the line that says 'allow=127.0.0.1'
Change it to 'allow='
Press CTRL+X to close out of nano and save the file
Run sudo /etc/webmin/restart

After that you should be able to login from other machines.
[/INDENT]

---

