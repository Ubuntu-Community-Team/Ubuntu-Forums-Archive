---
title: "can't see the network printer"
date: 2006-06-02
forum: Desktop Environments
---

### Post by chbenito on 2006-06-02
So, I have a small office with two computers and a printer
on the network. The printer is a Dell 3100cn. The windows
box sees the printer and works fine. The linux box does not.

I have reinstalled cups. I have installed the driver rpm that
came with the printer (via alien).

I marked 'Detect LAN Printers' on the 'Global Settings' menu.

I've fussed with all the things I can see and nothing seems
to work.

Any advice?

---

### Post by GoldBuggie on 2006-06-02
maybe
```
sudo /usr/share/cups/enable_browsing 1
```

---

