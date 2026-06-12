---
title: "Installed DE not showing on client EasySSH connection"
date: 2022-02-06
forum: Desktop Environments
---

### Post by camaban on 2022-02-06
Hello, newbie to the forum here. I use Ubuntu Studio and a two other Ubuntu derived distros as a desktop, and have just began using Ubuntu Server as an ongoing project to see where it takes me.

I have installed LXDE-core to aid me as I get to grips with it, but plan to disuse it going forward and get more confident with the terminal. The DE works fine when monitoring it directly, but when I access it via EasySSH I do not see the DE, but only the terminal.

I have made sure that X11 forwarding is enabled in Ubuntu Server, but cannot get the DE to work headlessly.

Any ideas what I'm doing wrong?

Thanks.

---

### Post by schragge on 2022-02-06
[SSH X11 Forwarding Of Gnome-Boxes Under Wayland & Mixed Wayland & X11 Environments](https://dbts-analytics.com/notesxfwdgb.html)

---

### Post by camaban on 2022-02-06
I installed Gedit on the server through the client's ssh as a test, and I'm able to get a GUI for Gedit from the server, so must be something silly that I'm missing here.

---

### Post by uninvolved on 2022-02-06
I don't understand (as I've never looked deeper) completely why, but not all applications can have their GUI forwarded. It's something to do with ownership and permissions.

Anyhow, if I'm reading you correctly, you're trying to forward the entire GUI - as in forward the desktop? SSH doesn't do that. For that, you'll want something like VNC or maybe even TeamViewer - which works well but is proprietary. x11 forwarding only works with individual applications.

---

### Post by camaban on 2022-02-07
Ahhh, yes you read me correctly, I'll have to familiarise myself with VNC.
Thanks

---

### Post by camaban on 2022-02-07
Also, just as a follow up, I have installed and am using Remmina which is an open source alternative, and seems to work well.

---

### Post by uninvolved on 2022-02-08
Remmina is a solid project. Glad you got it working okay for you. I can agree with your thinking. x11 forwarding is no substitute for a full remote desktop environment. Given the chance, I definitely prefer a Remmina type solution for many things.

---

### Post by ActionParsnip on 2022-02-09
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-20-04)

---

