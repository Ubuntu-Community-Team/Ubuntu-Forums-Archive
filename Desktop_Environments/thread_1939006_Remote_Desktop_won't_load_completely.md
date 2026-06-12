---
title: "Remote Desktop won't load completely"
date: 2012-03-10
forum: Desktop Environments
---

### Post by luckymoonboy1 on 2012-03-10
Hello all! 

I am running into an interesting error. I'm trying to remotely connect to the currently running desktop session in Ubuntu 11.10 from Windows 7. I've tried several different tutorials and examples. I have never been able to connect to the running session, but I have been able to connect to a separate session before.

Now here is where the new error occurs. I tried again today and now I cannot get even a new session load. I can use the remote desktop client in windows to log in via the sesman-Xvnc module, it will do its little console thing where it says successful and all that then it loads a mouse and my background and sits there. I thought at first it was just taking time to load but I've waited over an hour. I have tried it with both the Ubuntu Classic desktop as well as Unity.

Both computers are on the same local area network, and I know they can communicate as I use the ubuntu computer to run a Minecraft server(not running when I tried to remote).

I have googled endlessly and searched the forums. But I have not found quite an error like it. I will greatly love any help that can be provided. Thank you!

---

### Post by steveferson on 2012-04-01
I'm having the same problem.

Can't get TightVNC to connect at all, and when using RDC I can only get to a blank desktop.  No icons down the left, no dash, no taskbar (or whatever the Ubuntu equivalent is) across the top.

I'm guessing the fancy new unity theme can't be delivered over RDP and it's just not able to fall back gracefully, so will it make a difference if I can figure out how to switch this off?

Fedora worked fine - but Wake on LAN wasn't working so I came to Ubuntu.  It doesn't work with RDP at all :(

---

