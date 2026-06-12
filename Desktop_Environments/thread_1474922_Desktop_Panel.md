---
title: "Desktop Panel"
date: 2010-05-06
forum: Desktop Environments
---

### Post by kawshik84 on 2010-05-06
Hi,

I am new to Ubuntu. Just installed it today. By mistake I removed all the panels on the top of the desktop which had my username, time date and the other stuff.

Hows do I get those back? Is there a restore option?

---

### Post by ajgreeny on 2010-05-06
Right click in your current lower panel and choose **New Panel**.  Now either drag the new empty panel to the top, or right click in it and choose **Properties** where you can set it to top, bottom left or right as you want.

Now you can add various things to it by another right click and choose **Add to panel**.  By default there is a menu bar, logout applet, clock, and launchers for Firefox and Evolution, if I remember correctly.  You can, of course add whatever you want, or you can do as I do and add everything to a single panel at the top, bottom or one side.

There is no simple restore facility, I'm afraid; once it's gone, it's gone, so you just have to start again.

---

### Post by finlost on 2010-05-06
> **jamieleshaw said:**
> Don't know if this is helpful but I will put it in anyway.
To Reset Panels type
rm -f ~/.gconf/apps/panel
then type
sudo /etc/init.d/gdm restart
;).

---

### Post by playinpearls on 2010-05-09
To Reset Panels type
rm -f ~/.gconf/apps/panel
then type
sudo /etc/init.d/gdm restart


this worked! but i had to manually delete the panel folder. it ouldn't let me in terminal.

thanks~

---

