---
title: "Is it actually possible to remotely control a headless 10.04 PC?"
date: 2011-02-20
forum: Desktop Environments
---

### Post by user68 on 2011-02-20
I've followed so many guides to do this and failed, I'm wondering if it's actually possible...

I have 10.04 AMD64 running with Gnome and I want to remove the monitor then remotely access it from inside my LAN through Snow Leopard (preferably) or Windows (if I absolutely have to) to control the 10.04 PC.

I've been able do it using Chicken of the VNC and NX Client and it works perfectly for me until I remove the monitor. Then I find neither of these clients will connect until after I reattach the monitor and Start X at the command line.

Can anyone please tell me what I must do to get around having to reattach the monitor every time, if indeed it's actually possible to?

---

### Post by wizard10000 on 2011-02-20
Neither VNC nor NX are X clients, they're remote desktop applications and X has to be running on the host for either of them to work. All they do are pass screen scrapes back and forth between host and client - no screen, no VNC  :D

If all you want is command line you should be able to just SSH into the machine but if you want a GUI client for a headless host then you've got to install an X client on the client machine.

Hope this helps -

---

### Post by user68 on 2011-02-20
Thanks for putting me on the right track Wizard10000, I did a search on X11 and managed to get it working by installing Xnest. Then on the Mac in the X11 terminal window:

ssh -X "user"@"ipaddress"
gnome-session

---

