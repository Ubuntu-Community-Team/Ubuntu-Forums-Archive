---
title: "awesome window manager crashes X after upgrade to koala"
date: 2009-11-15
forum: Desktop Environments
---

### Post by orengolan on 2009-11-15
After I upgraded to Koala, X crashes when I try to open a terminal with awesome.  This is awesome 3.3.4 (comes with koala).
I don't use a graphical login manager. instead I simply type startx in the terminal.

I have 1 line in .xinitrc:
```
awesome
``` 

Also, I copied the rc.lua filed from /etc/xdg/awesome/ to ~/.config/awesome/
and awesome -k tells me my config file is ok.

grep EE /var/log/Xorg.0.log
```
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load module "type1" (module does not exist, 0)
(EE) Failed to load module "freetype" (module does not exist, 0)

```

---

### Post by orengolan on 2009-11-18
update - I just installed 9.10 and the same issue happened with a graphical login manager (i think it's gdm, whatever comes with xubuntu).

I also reported the issue on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/awesome/+bug/483295](https://bugs.launchpad.net/ubuntu/+source/awesome/+bug/483295)

any help will be great.

---

