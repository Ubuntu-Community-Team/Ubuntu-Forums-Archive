---
title: "Run application (boxee) at login, after network up"
date: 2010-09-27
forum: Desktop Environments
---

### Post by apoth on 2010-09-27
I'd like Boxee to run at login (GDM's set to go straight in when the machine boots) but I need it to run after the wireless network has negotiated a connection, otherwise boxee freaks out that there's no network and refuses to work even after the network's come up.

Can someone help with how to do this? I had a go at putting a script in a few of the /etc/network/if-up type folders but none of them were executed.

TIA.

---

### Post by apoth on 2010-09-29
I got around this by using a wired connection to a switch, with a wireless bridge off the switch..!

---

