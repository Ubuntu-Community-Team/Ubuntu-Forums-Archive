---
title: "printer networking problem, it dosn't work"
date: 2009-02-24
forum: General Help
---

### Post by 999alfred on 2009-02-24
I have two ubuntu systems running, a 7.1 and a 8.04, with a Brother laser connected the 8.04, i.e. the server. The printer works great on the local host and works via samba top my xp laptop, no problems, I just cannot get it to work via cups from my 7.04 system.The printer name is HL-1440, the printer's model number.

I first tried the old way I did it under Slackware went through firefox to url localhost:631 and set it up to ipp://192.168.1.205/printers/HL-1440. It cam back with the green indicator on the printer like everything was ok, but it wasn't. Try a test page and you get a continuous " Network host 192.168.1.205 not ready, trying again in xx seconds". not good.

So I delete the printer and go through ubuntu System->Printing and select ipp protocol. But, no matter what I enter in the host field:
192.168.1.205
192.168.1.205/printers
etc.

It never finds any queues.

SO, what the heck is the problem. client side, server side? I mean, windows can print to it, but not another linux system. Now that's a switch.

tj

---

