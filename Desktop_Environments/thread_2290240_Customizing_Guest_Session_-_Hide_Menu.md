---
title: "Customizing Guest Session - Hide Menu"
date: 2015-08-10
forum: Desktop Environments
---

### Post by versoph on 2015-08-10
Ubuntu desktop 14.04

I am customizing the guest session and have it mostly working. I've created [COLOR=#333333][FONT=monospace]/etc/guest-session/auto.sh[/FONT][/COLOR] ( thanks to other posts :) ) that launches the only application that he/she uses and I don't want to show the left menu. Any way to do this?

Thanks

---

### Post by TheFu on 2015-08-11
Load **openbox** and remove Unity as a starting point.  It would probably be best to start with an Lubuntu install to avoid all the bloat. Then just use openbox and not lxde.  You will want to remove or replace the right-click context menu in openbox.

---

