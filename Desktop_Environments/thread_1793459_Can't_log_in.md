---
title: "Can't log in"
date: 2011-06-29
forum: Desktop Environments
---

### Post by Francesco312 on 2011-06-29
I have had Ubuntu on my (approx. 4 year old) laptop since Karmic, and regularly upgraded to the newest version.
As I don't like unity, I tried to turn my Ubuntu into Xubuntu. So, I installed xubuntu-desktop from the official Ubuntu ppa. Now, I have the Xubuntu-style GDM, a "xubuntu" splash screen and so on; I can select both xfce session and xubuntu session from GDM.
But every time I try to log in using either "XFCE" or "xubuntu" session, the xorg server crashes, and I return to GDM (in a different terminal).
Also trying to execute init 5 -> startxfce4 from recovery console was not successful.
The only thing I managed to do was to log in as root from root recovery console.

Here are the logs I get:
- from dmesg, after I try to log in from GDM:
> [  919.671825] xfce4-session[3005]: segfault at 0 ip 003cdf63 sp bf95b070 error 4 in libxfce4util.so.4.1.1[3c6000+d000]- when I try to run startxfce4, I get: [http://pastebin.com/aj3rUtZ0](http://pastebin.com/aj3rUtZ0)

All other sessions (kde-plasma; gnome; unity...) work correctly.

The only thing I found, googling, was [http://superuser.com/questions/246872/cant-login-into-fedora-14-xfce-desktop-for-the-second-time](http://superuser.com/questions/246872/cant-login-into-fedora-14-xfce-desktop-for-the-second-time) , but it didn't help

Uninstalling, purging, reinstalling, removing configuration files (I deleted both ~/.config/xfce4 and ~/.cache) did not change anything.

I tried to copy the ~/config/xfce4 folder from a working xubuntu system (an older pc where I have directly installed xubuntu natty), but that was of no use either.

Do you have any ideas on how I can get xfce working? What further information should I provide?

TIA

---

