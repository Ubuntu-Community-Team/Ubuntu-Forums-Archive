---
title: "Gnome 'forgets' compose key position"
date: 2008-09-17
forum: Desktop Environments
---

### Post by metafractal on 2008-09-17
Hello,
I am having a strange problem with Gnome. I am able to set up a compose key by in Gnome under Ubuntu 8.04 by going into settings -> preferences -> keyboard -> layout options. The compose key then works until I reboot, after which ubuntu seems to 'forget' the setting and typing with the key produces no result. The funny thing is, when I go back into the layout options after a reboot, the left win key for the compose settings is still checked, and it will start working again if I un-check and re-check it but not otherwise.

Any ideas? It's annoying having to re-set it every time.

P.S. I've tried it with other keys than the left-win key and it still does the same.

---

### Post by ffahog on 2009-01-10
Bump. I'm having the same issue—can anyone help?

---

### Post by mr_guy99493 on 2009-10-16
Same problem for me too.
Im going to try adding an xmodmap definition of the multi_key instead of doing it through the gui. Might work, havent tried yet.

---

### Post by sethtriggs on 2009-10-21
> **mr_guy99493 said:**
> Same problem for me too.
Im going to try adding an xmodmap definition of the multi_key instead of doing it through the gui. Might work, havent tried yet.

How do you do that, as I am having the same problem. What xmodmap definition would you use to ensure that the Compose key stays in place and where do you enter it?

-Seth

---

### Post by foresto on 2009-10-22
XFCE doesn't offer a GUI for this, so I change it by editing /etc/default/console-setup to contain this line:
XKBOPTIONS="compose:ralt"
(and then restart X)

To discover which keys you can use other than Right Alt, run:
grep compose: /usr/share/X11/xkb/rules/xorg.lst

More info:
[https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)

---

