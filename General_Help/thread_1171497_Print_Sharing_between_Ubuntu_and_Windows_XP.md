---
title: "Print Sharing between Ubuntu and Windows XP"
date: 2009-05-27
forum: General Help
---

### Post by vDub2000 on 2009-05-27
I'm having trouble sharing my printer that's on a Ubuntu PC and allowing a Windows XP laptop to print from it. I've been doing some Google searching, and what I've found isn't helping me out.

The problem is that when I try to connect to my printer from the Windows XP machine, it's acting like it can't even find it even though the printer is being shared and the URL is correct.

Can someone help me fix the issue?

---

### Post by ghen on 2009-05-27
XP Doesn't read linux shares by default. On a real server you could install Samba to talk to XP machines. Samba at its base its just allowing windows to see things on a linux machine like printers and file shares.

Now from a desktop perspective I don't know if there is a better way (something with a GUI for example) but this would do the trick in a command line setup.

[https://help.ubuntu.com/8.10/serverguide/C/samba-printserver.html](https://help.ubuntu.com/8.10/serverguide/C/samba-printserver.html)

> The default Samba configuration will automatically share any printers installed. Simply install the printer locally on your Windows clients. 

---

