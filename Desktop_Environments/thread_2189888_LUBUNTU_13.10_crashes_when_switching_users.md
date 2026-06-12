---
title: "LUBUNTU 13.10 crashes when switching users"
date: 2013-11-24
forum: Desktop Environments
---

### Post by CWMAR30 on 2013-11-24
When switching users while another user is logged in Lubuntu 13.10 when going to the LU menu then LOGOUT then SWITCH all I get is a black screen with a __ flashing on the screen. I am here to find out why that is happening and what I can do to fix it to get back into  Lubuntu without having to restart?

I had to shut the computer down to get the graphical end to come back up. =[ Linux is my only choice this is a coustom built computer and can only install via USB

This computer had XUBUNTU 13.10 on it but the icons not staying in place when logging out and log in and they're in a different location everytime drove me nuts so I purged Xubuntu and installed Lubuntu instead of a reinstall. 

Thanks,
Christopher 

Lubuntu 13.10
2 gigs of ram
Coustom Built PC.

---

### Post by dave35 on 2013-11-24
Maybe a stale file-lock, boot to the BASH prompt and as root delete the contents of /tmp/, check if the other user has read/write access to /tmp. Or it maybe a corrupt .Xauthority file in the users home dir, delet it and restart the computer ..

---

