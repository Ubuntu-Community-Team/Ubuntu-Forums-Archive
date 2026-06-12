---
title: "How to set default gdm-session by CLI?"
date: 2007-03-14
forum: Desktop Environments
---

### Post by frafu on 2007-03-14
Hello, 

I have a headless server that I also use to learn about linux. 

I installed ubuntu on it; later I added the kubuntu-desktop and xubuntu-desktop. Unfortunately, I am not able anymore to connect to the vino vnc server, because on startup, I think (because of the process list I get when ssh-ing into it) that the computer launches the xfce desktop. 

Could anybody please tell me how I can set it to start genome as default? 

I think that gdm is being used, though kdm and xdm are also installed. Does this matter? 

Many thanks in advance. 

Francesco

---

### Post by zvacet on 2007-03-14
On login screen go to sessions  and choose GNOME.You will be asked is it for that session    only or default.Click on default.

---

### Post by frafu on 2007-03-14
Thanks for the reply. 

Unfortunately, I don't see the login screen as the computer is headless. The best would be if I had a command that I could give through ssh to set gnome as default session. 

Francesco

---

### Post by frafu on 2007-03-14
I finally succeeded to do it the way zvacet indicated by using a remote connection through nx and choosing xdm in the configuration of the nx-client. This way, nx showed me the login window.

---

### Post by diskotek on 2008-04-19
```
dpkg-reconfigure gdm
```

---

### Post by x1a4 on 2008-04-20
Hi,

Edit the ~/.dmrc file like so
```

[Desktop]
Session=*session*

```

Where *session* is the executable of the session. For Xfce this would be: 
```

[Desktop]
Session=xfce4

```

You can also add the default language in ~/.dmrc.  For example: 
```

[Desktop]
Session=xfce4
Language=en_CA.UTF-8

```

---

