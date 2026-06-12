---
title: "To change Screen Resolution in Ubuntu using Terminal"
date: 2009-04-15
forum: General Help
---

### Post by Durgacharan on 2009-04-15
Hi,

It's now showing Input signal error once I logged in to Ubuntu using user name and password And it happened after I changed my screen resolution to a bit high resolution.

Please help me to get back to my previous setting.

Regards,
Durgacharan

---

### Post by khelben1979 on 2009-04-15
Please post your contents of your /etc/X11/xorg.conf file to this thread.

Since you're using Linux you have the possibility on running several x servers at once, so try this from a text console:

```
sudo startx -- :2
```
starts another x server which you can see with: ```
ctrl + alt + f8
```

If this works you have a working x server with working graphics.

---

