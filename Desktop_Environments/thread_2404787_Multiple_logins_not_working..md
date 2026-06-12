---
title: "Multiple logins not working."
date: 2018-10-28
forum: Desktop Environments
---

### Post by tdiguy2 on 2018-10-28
Some background on this. It is a headless ubuntu 18.04 lts system. I primarily access it via ssh. Sometimes i do things i really prefer to do through a gui, like partitioning a drive and deleting entire directories ( not sure why but i just really prefer to do those operations via gui ). So I have user A and user B. I also generally use ssh tunneling because its pretty simple easy and requires no software installed to use remotely. So i ssh in remotely with user A no issues can connect and such without a problem. Then i try opening a RDP session with user A, I get the xrdp login screen, log in and then the rdp window closes. If i log in to RDP with User B I am able to log in without an issue and it is even using xfce4.

I am not sure what is going on with this, or if this is simply working as intended and if so is there a way i can circumvent it anyway?

---

### Post by TheFu on 2018-10-28
I do it this way:```
#!/bin/bash

XTERM_OPTS="-u8 -fs 18 -fa Monospace -sb -fg green -bg black"
uxterm -geometry 80x25+0+0 $XTERM_OPTS -e ssh -X remote-userid@remote-server &
```

Just use a different userid and server location as needed.  
The client ~/.ssh/config file is completely supported for session setting, different ports, different userids, and aliases.

---

