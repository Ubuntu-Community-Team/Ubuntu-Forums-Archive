---
title: "Unable to Configure NVIDIA"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by rykel on 2007-10-25
Hi,

I deleted my /etc/X11/xorg.conf and all its backup files.

Now, when I try to configure the NVIDIA driver, it gives me the expected error message. (see screenshot)

What can I do to restore the default Gutsy Gibbon xorg.conf file?

---

### Post by xjpvictor on 2007-10-25
try this:
> sudo dpkg-reconfigure xserver-xorg

---

### Post by rykel on 2007-10-25
> **xjpvictor said:**
> try this:

Tried... many times... the system would try to log into a low-res mode ("640xSomething")... only way to get my native res (1280x800) is to NOT use the official NVIDIA driver.

 I am thinking, how can I check if Compiz fried my NVIDIA card?

---

### Post by shad0w_walker on 2007-10-25
Compiz is not going to have fried your card. Like the error says, you have a missing file, no damage to your hardware. What you want in an ideal world is you get the xorg.conf file back, best way is use the command mentioned earlier to generate a standard, basic xorg.conf file that the display control panel can use. Then setup the screens the way you want in the display manager.

---

