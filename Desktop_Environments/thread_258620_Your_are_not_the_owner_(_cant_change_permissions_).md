---
title: "Your are not the owner ( cant change permissions )"
date: 2006-09-16
forum: Desktop Environments
---

### Post by stwebs on 2006-09-16
I have justinstalled ubuntu on my pc, im updateing all i can .. when it came to install flash and java manuly into my usr/lib/mozela-firefox (or whatever the path is..) it wont let me paste the libflashplayer.so or any otherfiles in there, it says im not the owner ???? #-o 
 I installed ubuntu, i should be the owner..:confused:   any help would be helpfull..

ps im not a linux expert.. i came over from win xp ](*,) 

thanks..
Mike

---

### Post by ayoli on 2006-09-16
as user you only own your homedir (/home/your_username). you must have super user(root) rights to access these folders (and some other)
you have to use sudo, read thiese pages:
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

for ex, to install flash in a terminal type in:
```

sudo /path/to/flash_install_script
```
you will be prompted for your **user** password

---

