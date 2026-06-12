---
title: "Dial Problem"
date: 2006-02-06
forum: Desktop Environments
---

### Post by XIII on 2006-02-06
I'm using Gnome, my connection is DSL PPPoA connection through Speedtouch USB Modem, i did setup my internet connection as a daemon, and it works good, but when the connection get down i need to restart my pc in order to dial it again, what is the way to dial it on the system so i don't need to restart, i need to know how to connect and disconnect my pc as sometimes i need to disconnect it.

---

### Post by jasmuz on 2006-02-06
$ sudo /etc/init.d/networking restart

That should restart your networking services in a jiffy!

---

### Post by XIII on 2006-02-06
My connection is a direct USB connection not through a LAN, so this doesn't work with it, i even stopped it by: $ sudo /etc/init.d/networking stop and the connection is on still.

---

### Post by jasmuz on 2006-02-07
Does unplugging and reconecting do anything?

---

### Post by XIII on 2006-02-07
No, and always i have no other choice than restarting the pc.

---

### Post by jeffreyvergara.NET on 2006-02-09
hi, I also use Speedtouch 330 ADSL Usb modem.

I figured out how to reconnect without restarting your PC

> sudo /etc/rc2.d/S95dial start


now, the only thing that I need to know is how to automatic reconnect.

---

