---
title: "Screen Crashes"
date: 2005-12-11
forum: Desktop Environments
---

### Post by Minardi on 2005-12-11
Im just new to linux, and i just installed Ubuntu on a Intel Celeron 300 Mhz. With a graphics card of [COLOR=Blue]S3 TRIO V64+[/COLOR]. 
I start ubuntu, and it loads the clock etc. But then im at the login screen (that i can't view), and then i see a blue screen with all colors of the rainbow.

I can come in a commando screen with crt+alt+f1, but i don't know what to do there.

How can i solve this problem? I now can't do anything with this distro.
Thanks for ya help.

Minardi,

---

### Post by astoltz on 2005-12-11
after you ctrl-alt-f1, login with your normal userid, password.  Then do the command ```
sudo /etc/init.d/gdm stop
``` It will ask for a password - enter your's again.  After that do ```
sudo dpkg-reconfigure xserver-xorg
``` and be sure you've got the right video card / driver selected.

---

