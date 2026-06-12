---
title: "ssh user permissions skewed"
date: 2009-05-26
forum: General Help
---

### Post by daddysmonsters on 2009-05-26
Ok so I am running an ssh server. I created a new user using  "adduser NAME NAME"  Then I set the passwd and it works. The user can login remotely via ssh. However initially the user is presented with 

"Could not chdir to home directory /home/NAME: no such file or directory"

So I sudo mkdir NAME in /home and chown it to NAME. 

Well the user doesn't get the error anymore but ls does not work he can't perform many commands, (can finger for example) He cannot sudo either. Now I need to set him up to be able to sudo to root. I also noticed that when I log in myself either physically at the server or remotely via ssh I get a proper username@servername he gets a simple $   

Any help here? I have asked around a bit but what I do not want is to allow remote root login (su is fine once connected) Also I am running Ubuntu server installation jaunty
[SIZE=3]
[/SIZE]

---

