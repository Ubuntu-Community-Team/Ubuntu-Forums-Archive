---
title: "Newbie problems getting on the net"
date: 2005-07-04
forum: Desktop Environments
---

### Post by Nturck on 2005-07-04
Help please I have installed v5.04 all ok.
The computer can see my network I can ping out and ping the ubuntu machine ,also I can ping external servers from my ubuntu machine . BUT. I can not make firefox work it comes up as address unknown .
so close and yet so far....... What else do I need to alter ? 


All suggestions gratefully received


Nick

---

### Post by Knome_fan on 2005-07-04
Sorry, I can't realy help you, but I think it would be much easier for people to actually help you if you gave us some more information.

For example, how exactly are you connectiong to the net? Are you using a router? If so, did you set a default route? What's in your /etc/resolv.conf?

Good luck!

---

### Post by godzero on 2005-07-05
Are you pinging by name (google.com) or ip address?
If you can ping by name, but not able to browse by name, that would be odd. (firewall?)

If you can't ping by name, check your dns lookup settings, compare then to a differnet machine. Where I am, the dhcp/dns servers have a habit of going black from time to time, so I usually have a backup plan.

---

### Post by kagashe on 2005-07-05
Hi,

I am also having this problem but I have temporarily resolved it by opening Firefox through "sudo firefox"

You can also try this.

kagashe

---

### Post by godzero on 2005-07-05
Ah yes, I remember installing firefox from the fire fox site on a different distro.

Once installed, the first run had to be done as root, so it could import some settings and plug-ins from mozilla or netscape.

Are you using the ubuntu package, or another?

I have firefox from an ubuntu repository, and it runs fine.

---

### Post by IchBin on 2005-07-05
[QUOTE=Nturck]Help please I have installed v5.04 all ok.
The computer can see my network I can ping out and ping the ubuntu machine ,also I can ping external servers from my ubuntu machine . BUT. I can not make firefox work it comes up as address unknown .
so close and yet so far....... What else do I need to alter ? 


All suggestions gratefully received


Nick[/QUOTE]
 You probably need to disable ipv6 in your Firefox config. Open up a tab in firefox and type about:config in the address bar. Look for the line **network.dns.disableIPv6** and change it to true. I had the same problem and that fixed it for me.

---

### Post by Nturck on 2005-07-06
Thank you ,
The config in firefox did the trick , one for the record.

---

