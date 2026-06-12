---
title: "Turning the GUI off and logging in remotely"
date: 2009-01-18
forum: General Help
---

### Post by Arukas on 2009-01-18
I am turning my computer into a gateway/router/firewall and maybe more.  I am doing this for the learning experience and fun.

I read, if I can get the bios not to freak out, I can run the computer without a mointer/keyboard and do a remote log in.  One of the things I read was having a system like that, its a good idea turn the GUI off.  This may be a gross missunderstanding.

What I want to know, is SSH all I need to do a remote loggin?  And how do i turn the gui off? after I finish everything, I want to do.  Or if I have misunderstood what I am doing please let me know.

---

### Post by mssever on 2009-01-18
> **Arukas said:**
> I am turning my computer into a gateway/router/firewall and maybe more.  I am doing this for the learning experience and fun.

I read, if I can get the bios not to freak out, I can run the computer without a mointer/keyboard and do a remote log in.  One of the things I read was having a system like that, its a good idea turn the GUI off.  This may be a gross missunderstanding.

What I want to know, is SSH all I need to do a remote loggin?  And how do i turn the gui off? after I finish everything, I want to do.  Or if I have misunderstood what I am doing please let me know.
Yes, SSH is adequate if you're comfortable on the command line. You might also be interested in webmin or similar. To stop the GUI, run ```
sudo service gdm stop
``` If you want to uninstall it, do ```
sudo aptitude remove gdm
```

---

