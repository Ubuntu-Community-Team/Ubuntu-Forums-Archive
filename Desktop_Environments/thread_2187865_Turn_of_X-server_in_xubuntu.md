---
title: "Turn of X-server in xubuntu"
date: 2013-11-14
forum: Desktop Environments
---

### Post by reg2 on 2013-11-14
Im trying to install new graphics drivers from Nvidia but get a message i need to turn off the x-server. I have tried both of the below actions but they do not work. What else can i do?

sudo service lightdm stopsudo service gdm stop

---

### Post by grahammechanical on 2013-11-14
I have never done what you are trying to do but I do know a couple of things

1) GDM is not used by Xubuntu.
2) We should run sudo service lightdm stop before we run the command to install the Nvidia driver.
3) After installation of the Nvidia driver we run sudo service lightdm start.

I am repeating instructions I was given by someone who knows this stuff. But I have never felt the need to do it. Are you running these commands in the terminal or in a tty? I do not know if it makes any difference.

Regards

---

### Post by Bucky Ball on 2013-11-14
Well, lightdm is for Unity as far as I know and gdm is for Gnome.

Try turning off xfce4 or something like it. You could also try a bit of research before posting.

[https://duckduckgo.com/?q=turn+off+x+server+xubuntu](https://duckduckgo.com/?q=turn+off+x+server+xubuntu)

(In xfce4, startx will get you to a desktop, incidentally, NOT lightdm).

---

