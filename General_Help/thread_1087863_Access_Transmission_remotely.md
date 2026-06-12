---
title: "Access Transmission remotely"
date: 2009-03-05
forum: General Help
---

### Post by fatnic388 on 2009-03-05
I'm trying to access Transmission remotely. It works fine on my local network which is great. But how can I access it from outside of my network? (ie. allow any remote IP address to access Transmission?)

---

### Post by The Joe on 2009-03-05
Instead of using your LAN address you just visit YourIP:YourPort

If you don't know what your IP is try a site like whatismyip.com or check your router/network settings.

---

### Post by fatnic388 on 2009-03-05
OK. Got it now. Forgot to set up port forwarding in my router setup. All ok now. 

Thanks.

---

### Post by andrewbrown22 on 2009-03-05
Wait, how do you set this up? Is this so that you can access it from a web browser?

---

### Post by The Joe on 2009-03-06
Yes, I believe Transmission has a Web GUI similar to Windows's uTorrent program. If you're more familiar with that - uTorrent apparently works superbly under Wine.

---

### Post by mªrty on 2009-03-06
I just use VNC, since there are web-based clients available for free and offers full access to the OS. just my 2 cents.

---

### Post by bodhi.zazen on 2009-03-06
My 2c : ssh + rtorrent + screen :twisted:

---

