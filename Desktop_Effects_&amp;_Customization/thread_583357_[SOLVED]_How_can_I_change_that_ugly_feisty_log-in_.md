---
title: "[SOLVED] How can I change that ugly feisty log-in sound(clip) back to that of dapper?"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by offline on 2007-10-20
Now that I managed to have sound I wonder if...Can I change this login sound of feisty back to that of dapper?

---

### Post by ddrichardson on 2007-10-20
I don't know where you will get the required sound file from but changing it is [easy.]("http://www.howtogeek.com/howto/ubuntu/disable-the-login-sound-on-ubuntu/")

---

### Post by offline on 2007-10-20
Thanks anyway.

I found and successfully implemented a(simple) way. Just reboot with a live dapper cd, insert a usb flash disk and sudo copy /usr/share/login.wav. Then reboot to normal feisty, sudo cp your file to a directory. 

Than from the system>preferences>sound just choose your new sound file. For me, it worked.

Logout.wav though didn't work(probably logs out faster now?)...

---

