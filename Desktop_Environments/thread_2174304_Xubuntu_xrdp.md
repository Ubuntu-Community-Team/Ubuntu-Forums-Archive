---
title: "Xubuntu xrdp"
date: 2013-09-13
forum: Desktop Environments
---

### Post by Matthew_Stiverson on 2013-09-13
I recently had issues with my Ubuntu install where I was getting an error that the system was running in low graphics mode. I finally got tired of messing with it and decided to go with Xubuntu rather than regular Ubuntu since I am not a fan of Unity. I am working on getting XRDP setup to my liking. I first had to fix the tab issue by removing the <Super> Tab entry. I am now trying to get my desktop to display like the xubuntu session and not the xfce session. I did a printenv from the desktop and from xrdp and I noticed the DESKTOP_SESSION variable was different. I tried editing the /etc/xdg/xfce4/xinitrc file where it has DESKTOP_SESSSION="xfce" to DESKTOP_SESSION="xubuntu" but it did not make a difference. Is there somewhere in a profile that I can set the xubuntu session as the default for xrdp? It is not that big of a deal to get it working but it would be nice to have it the same on both the desktop and xrdp.

---

### Post by cmcanulty on 2013-09-14
as long as you have xfce and xubuntu both installed already-log out then choose the one you want from the icon by sign in box, system will remember your choice in future

---

### Post by Seanon on 2013-09-27
I don't think that is what he was asking about, the OP was asking how to get the default session changed from "XFCE" to "Xubuntu" for XRDP ONLY, this is something I am looking for as well, when I log into my server, the default desktop is xubuntu, BUT when I log in via XRDP, I am forced to log in to the GNOME session, which I had to install because it refused to log in via xrdp at all until the gnome session was installed...

---

### Post by bsrgsit on 2014-01-27
Hi , I am able to install and connect using xrdp but after connecting i can see only blank screen. please help

---

