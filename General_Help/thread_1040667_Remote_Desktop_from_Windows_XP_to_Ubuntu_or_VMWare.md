---
title: "Remote Desktop from Windows XP to Ubuntu or VMWare"
date: 2009-01-15
forum: General Help
---

### Post by raiderleaf on 2009-01-15
Hello everybody, I have Win XP installed on my Laptop, and while I'm not at home, I'd like the ability to work on my desktop via remote desktop, except the operating I'm trying to RDP to is Ubuntu, which is the main OS on my desktop. I need it because I"m working on virtualization between Ubuntu and Win XP on that machine in particular, so it also would be really nice if I could have a way to conveniently RDP just my VMWare Server that I used to create that guest OS. Any ideas? I'm using Ubuntu 8.04 LTS on the Desktop and VMWare Server 2.0 on there as well running Win XP as the guest OS.

Thanks,

raiderleaf

---

### Post by redilyn on 2009-01-16
When you leave home start your virtual machine

If the guest os is configured correctly for RDP and is not firewalled you should be able to connect to it fine.

Most likely you will need to make changes to your port forwarding if your using a router. Be sure to forward the RDP port to the ip address of the guest os.

If you do not have a router, then just use the guest os ip when trying to connect with RDP

If you would rather connect to ubuntu directly you will need to install vncviewer or something compatible on your laptop and then enable remote desktop under System -> Preferences -> Remote Desktop

---

