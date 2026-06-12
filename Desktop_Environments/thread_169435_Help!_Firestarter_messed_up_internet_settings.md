---
title: "Help! Firestarter messed up internet settings"
date: 2006-05-02
forum: Desktop Environments
---

### Post by Ninjagecko on 2006-05-02
Hello.

Would anyone please help?

I installed Firestarter, set up internet connection sharing (ip masquerading), and then uninstalled Firestarter (sudo apt-get remove firestarter --purge).

problems:
1) Firestarter left my iptables in the wrong state, and every time I flush them they return misconfigured upon reboot.

2) Now I'm unable to use the internet unless I do "sudo ipmasq" every time I boot my computer.

Might anyone know how to fix this please?

I'd warn others against using Firestarter unless they really trust the software. =(

---

### Post by Foxmike on 2006-05-02
Hi!  If you don't mind asking, why did you uninstall Firestarter?

Personally, I just keep Firestarter running so then you keep the control on what's appening!  Anyway, if you still want to keep it removed maybe just a little scrip in /etc/init.d linked somewhere in /etc/rc2.d may fix it.  I don't know yet about scripting (still fairly newbee) but I'm pretty sure you can easily find good examples here: [http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://www.tldp.org/HOWTO/IP-Masquerade-HOWTO/)

Good luck!

-FM

---

