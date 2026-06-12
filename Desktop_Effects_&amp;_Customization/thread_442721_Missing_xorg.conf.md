---
title: "Missing xorg.conf?"
date: 2007-05-13
forum: Desktop Effects &amp; Customization
---

### Post by WaeV on 2007-05-13
Hi all,  I've been trying to install beryl for the past few days and after no luck on dapper I've decided to try it with feisty.  I was following this tutorial [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon") and installed the "open source ati driver" (mesa driver?)  to replace fglrx in order to use aiglx with beryl.  After I went through the apt-gets and such, I went to edit the /etc/X11/xorg.conf file and found it empty.  I did a file search and there was no xorg.conf file.  I tried lowercase and uppercase X's, copied the command, typed the command; nothing.  I even did a file search and the only things to come up that came up that looked like the xorg.conf (I remembered what it had looked like from dapper) were xorg.conf_disablectrlaltbackspacegnome and xorg.conf_disablenvidialogo.  My graphics work fine.  Before the fgl_glxgears had worked fine and with the new driver glx_gears works as well, so I know the graphics are working right, they just don't seem to look for/need the xorg.conf file.  I don't know how the end result will be affected if I just skip over the step...  And oh yeah I have tried rebooting.

---

### Post by WaeV on 2007-05-13
You know what, I think that this step was part of the optional step to manually change the fglrx driver to the open source one.  I'm not sure, so let me know if I'm wrong, but I might have solved the problem.

---

### Post by WaeV on 2007-05-18
It's weird though, I still have no xorg.conf file.  does the mesa driver use xorg.conf?

---

