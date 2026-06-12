---
title: "To know the desktop environment of the machine while logged into a remote machine"
date: 2009-04-23
forum: Desktop Environments
---

### Post by rajatm on 2009-04-23
Hi , 

I am logged into a remote machine using 'ssh' . Now if i launch any GUI based application it will use the x-server of the machine from which i have logged in. 
I want to know is there a way to find out from the remote machine ( in which we are logged in using ssh) the desktop environment of the machine form which we have sshed into the remote machine.

FYI: When you ssh into a remote machine the variables $DESKTOP_SESSION , GNOME_DESKTOP_SESSION_ID , KDE_FULL_SESSION are unset as you never know which Desktop session is there on that machine.

---

