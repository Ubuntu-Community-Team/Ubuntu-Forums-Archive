---
title: "display problems in Ubuntu....need urgent help"
date: 2005-12-04
forum: Desktop Environments
---

### Post by diffuser78 on 2005-12-04
Hi guys,

I was a happy Ubuntu user untill I shifted to Breezy from Hoary 2 weeks back. 

My only problem this time is that I see some patches on the screens and panels. These patches are generally of the theme which I am running.  Sometimes some lines appear on the desktop and if I refresh the desktop it goes away. After sometime they come back again.

My resolution and other things are fine except for this. Do I need some driver support or there is something else to this. I am happily runnig Breezy on my Laptop and my School Computer.

Any suggestions please. I am really frustrated by this bad dispaly ...please help me.

Thanks for your time,

---

### Post by dcstar on 2005-12-04
[QUOTE=diffuser78]Hi guys,

I was a happy Ubuntu user untill I shifted to Breezy from Hoary 2 weeks back. 

My only problem this time is that I see some patches on the screens and panels. These patches are generally of the theme which I am running.  Sometimes some lines appear on the desktop and if I refresh the desktop it goes away. After sometime they come back again.

My resolution and other things are fine except for this. Do I need some driver support or there is something else to this. I am happily runnig Breezy on my Laptop and my School Computer.

Any suggestions please. I am really frustrated by this bad dispaly ...please help me.

Thanks for your time,[/QUOTE]
Run this in a terminal and let it try and redetect your video card:

sudo dpkg-reconfigure xserver-xorg

---

### Post by diffuser78 on 2005-12-05
[QUOTE=dcstar]Run this in a terminal and let it try and redetect your video card:

sudo dpkg-reconfigure xserver-xorg[/QUOTE]

David, I tried it so many times but still no success. Still I see such patches. I am posting a screenshot for the same.

Please help me.

Daniel

---

### Post by diffuser78 on 2005-12-05
[QUOTE=dcstar]Run this in a terminal and let it try and redetect your video card:

sudo dpkg-reconfigure xserver-xorg[/QUOTE]

I am also attaching my /etc/X11/xorg.conf 

Can somebody please help me.

Thanks

---

### Post by heimo on 2005-12-12
I have no idea if this makes any difference, but I'd try to change sis driver to vesa to see if this is driver related problem. Then you can try with different color depths, 16, 24, 32.

---

