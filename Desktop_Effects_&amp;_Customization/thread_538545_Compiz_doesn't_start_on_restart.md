---
title: "Compiz doesn't start on restart"
date: 2007-08-30
forum: Desktop Effects &amp; Customization
---

### Post by simonfiction on 2007-08-30
Hi,
I've followed a [tutorial]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/") to install compiz and everything works fine. But whenever I restart my computer compiz isn't running and I have to run it every restart. 

How can I get it so compiz runs automatically?

Thanks,
Si

---

### Post by alan34 on 2007-08-30
Hi,
Go System - Preferences - Sessions

Click Startup Programs tag, then New and add Name and command

compiz --replace -c emerald &    
                         
is what I use

Log Out and try it:)

---

### Post by simonfiction on 2007-08-31
Thanks for that. Worked a treat.

Si

---

### Post by fwalderd on 2007-08-31
Hi,

I have tried to follow the advice but still Compiz doesn't start at login (however, the normal Gnome window decorations are gone, too;) ). I have to do System>Preferences>Desktop Effects to disable and re-enable the effects to make Compiz work, and then re-set the hsize value in gconf-editor to 4.

No idea where these settings are stored to make them permanent.

Cheers, Felix

---

### Post by Hyperkill on 2007-08-31
I was having major issues with compiz overall until I found this guide...

[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

I would suggest first going into synaptic package manager and searching for compiz.  Then remove everything with a green box next to it, even Desktop Effects.  Also, after following the above guide it was like I was in compiz heaven and everything worked beautifully.

---

