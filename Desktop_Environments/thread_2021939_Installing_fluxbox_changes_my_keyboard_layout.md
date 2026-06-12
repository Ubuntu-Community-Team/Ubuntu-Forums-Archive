---
title: "Installing fluxbox changes my keyboard layout"
date: 2012-07-10
forum: Desktop Environments
---

### Post by MadsRC on 2012-07-10
I've just installed a Ubuntu 12.04 Server, with OpenSSH & LAMP.

Then, because I need a small lightweight desktop for xRDP (The server is the only one accessible from WAN, so I need to access internal pages through it) I've installed the following packages:
[LIST]
[*]Fluxbox
[*]Xorg
[*]XDM
[*]Firefox
[*]xfe
[*]xRDP
[/LIST]

Now, when I RDP from my windows PC, my keyboard layout have changed to US. I haven't tried attaching a keyboard and screen to the server, cause I'm not at home right now, but I know that when I installed the server last night, the server did NOT have US keyboard...

Anyone know how to change the keyboard layout? I'd prefer a terminal way!

---

### Post by MadsRC on 2012-07-10
I've tried with setxkbmap <countrycode>, but seems that extension doesn't exist in v10

---

