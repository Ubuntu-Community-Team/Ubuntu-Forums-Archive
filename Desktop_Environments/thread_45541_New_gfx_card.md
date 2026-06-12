---
title: "New gfx card"
date: 2005-06-30
forum: Desktop Environments
---

### Post by Freddy on 2005-06-30
Hi all, just bought myself a new gfx card and was wondering what to do, can I just reinstall the nvidia drivers or should I remove the old ones first?

/Freddan

---

### Post by intangible on 2005-07-01
If you already had the nvidia drivers loaded and your new card is also a nvidia, just replacing the card should work :D  (You can edit /etc/X11/xorg.conf and change the device name to match your new card if you want, just make sure you name it identical in all sections, because they reference one another).

If you want to reconfigure it "just because" try this:

**sudo dpkg-reconfigure xserver-xorg**
and then 
**sudo nvidia-glx-config enable**

---

