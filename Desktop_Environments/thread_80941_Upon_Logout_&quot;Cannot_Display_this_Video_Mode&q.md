---
title: "Upon Logout: &quot;Cannot Display this Video Mode&quot;"
date: 2005-10-23
forum: Desktop Environments
---

### Post by fargusmax on 2005-10-23
Like the subject says, everytime I choose anything from the Logout Menu: Logout, Restart or Shutdown, etc.  I get this on my LCD.  Then nothing happens.  I am using the latest set of fglrx drivers from ATI using a HOWTO in another thread.  However, this happens when I'm using vesa also.  It's like it just can't get back to gdm.  gdm works fine upon bootup.

Hopefully someone knows what's going on with this (this was not a problem in Hoary, and SUSE 10 did not exhibit this problem either)

This is the only thing keeping me from using Ubuntu as my main OS on my main machine.

Rob

---

### Post by mykey on 2005-10-23
try taking out all resolutions you don't need in /etc/X11/xorg.conf in the screen section

---

### Post by fargusmax on 2005-10-23
[QUOTE=mykey]try taking out all resolutions you don't need in /etc/X11/xorg.conf in the screen section[/QUOTE]

Thanks for the quick response.  I just tried this, and still have the same results.

---

### Post by mykey on 2005-10-23
how about Strg+Alt+Backspace when it happens? can you get a terminal via the Alt keys or is it just a general freeze?

---

### Post by fargusmax on 2005-10-23
[QUOTE=mykey]how about Strg+Alt+Backspace when it happens? can you get a terminal via the Alt keys or is it just a general freeze?[/QUOTE]

I'm not sure what Strg is, but Ctrl+Alt+Backspace wouldn't restart X as it normally does.  Also, my keyboard's Numlock status light was frozen on, which says its a real freeze and not just display issue.  Is there a log somewhere I can try to find and post?

---

### Post by mykey on 2005-10-23
yes Strg is supposed to be Ctrl .. if it really hits the fan it will probably stop logging too, but look at /var/log/Xorg.0.log or/and /var/log/gdm/:0.log

---

