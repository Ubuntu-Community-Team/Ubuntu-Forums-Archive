---
title: "is there Remote Desktop Viewer in Ubuntu Netbook Remix"
date: 2009-05-01
forum: General Help
---

### Post by shva on 2009-05-01
It is in the "Internet" of normal Ubuntu. But I can't find it in my Ubuntu 9.04 netbook remix. If it is not in the system, how can I install it?  Thank you very much:)

---

### Post by dhughes on 2009-05-01
Remote Desktop is under Preferences using UNR 9.04

 I'm not sure if UNR 8.10 had it or not, I just used VNC, it works OK but if you view your PC from a netbook the screen looks pretty funky, it can't handle the colours or the resolution and it ends up looking fuzzy.

edit: btw the Remote Desktop password is short, so don't drive yourself nuts like me when I didn't notice my password was limited to only eight characters.

edit #2: Remote Desktop looks far better than VNC!

---

### Post by shva on 2009-05-01
There is a "Remote Desktop" under "Preference" but it is for sharing the local computer to a remote client. Actually I would like to have a reviewer to control another remote computer... But I can't find the "Remote Desktop Viewer" in my Ubuntu Netbook Remix. But I think you are right. There might be some questions about capabilities of netbook to handle the remote desktop ....

---

### Post by Brandon Williams on 2009-05-01
If you're trying to remote login to a Windows environment, you can install tsclient (which will pull rdesktop along for the ride).

If you're trying to get a VNC remote desktop, then install a vnc-viewer (I use xvnc4viewer, but xtightvncviewer is good, too. vinagre is the default in ubuntu-desktop).

None of these is defined as a dependency of ubuntu-netbook-remix, so they won't be installed for you.

---

### Post by shva on 2009-05-01
Thank you. Just get vinagre, and it works :)

---

