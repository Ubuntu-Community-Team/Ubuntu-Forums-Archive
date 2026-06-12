---
title: "Gnome remote desktop hung up. How to restart it?"
date: 2011-10-12
forum: Desktop Environments
---

### Post by alxlabs on 2011-10-12
System: Ubuntu 10.04LTS
Problem: Gnome remote desktop stopped responding but machine is working

Situation - I'm away from my ubuntu machine and using remote desktop to manage certain tasks. Suddenly Gnome remote desktop (vino server) stopped responding but I still have machine working normally otherwise, SSH is alive. Its not a network issue as it does not work even if I use VPN (VPN, samba, FTP etc everything is alive). I have a Windows XP based laptop with me using putty as SSH access tool and RealVNC viewer as VNC client. On top of that I want to avoid rebooting Ubuntu machine as I have several tasks running in the virtual machines which I won't be able to start if I don't have remote desktop.

Question 1: what is the less risky way to restart vino without rebooting? Is it even possible - I googled a bit but haven't find an answer, at least as how to do it just having a WinXP machine? In theory I can have X server commands forwarded thru putty, but then I need X on Win Machine... As an option I can try installing ubuntu on virtual machine within my XP laptop but this is hassle as I'm using mobile internet so cannot download huge things until I'm back home.

Question 2: Is it possible remotly (just using SSH from WinXP machine) to disable Gnome remote desktop (without having to reboot)? I want to istall/configure another VNC server, this is not the first time Gnome's built in one gives me troubles. Which one is the best alternative?

---

