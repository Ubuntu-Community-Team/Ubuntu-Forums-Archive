---
title: "Ubuntu and Lubuntu"
date: 2016-04-01
forum: Desktop Environments
---

### Post by asearle on 2016-04-01
Hi Everyone,

An older (retired) friend of mine has been using Ubuntu for a while but finds the Lubuntu menus more comfortable/familiar (i.e. like windows) so I activated the Lubuntu desktop for her (that worked fine by simply selecting in synaptic).

Anyway, everything works smoothly but she has a strange bar at the top of the screen.  My suspicion here is that this is the top-menu-bar which appears with Ubuntu (Lubuntu has a menu-bar which floats with each window).

Has anyone else experienced this?  Any idea how to get rid of it?

Many thanks,
Alan

PS: I'd like to keep both systems available and not de-install the ubuntu desktop.

---

### Post by vasa1 on 2016-04-01
> **asearle said:**
> ...
Anyway, everything works smoothly but she has a strange bar at the top of the screen.  My suspicion here is that this is the top-menu-bar which appears with Ubuntu (Lubuntu has a menu-bar which floats with each window). ...
You can attach a screenshot. That would help figure out what you mean.

Take the screenshot and then, when you're posting a response here, click on the paper clip icon above the text area and take it from there.

Without seeing anything, I'm guessing it's Lubuntu's own panel, lxpanel. Normally, what appears with Ubuntu shouldn't appears in a Lubuntu session and *vice versa*. That's a bit of an oversimplification but should do for now ;)

---

### Post by sudodus on 2016-04-01
Please tell us which version your friend is running: 14.04.4 LTS or some other version :-)

-o-

Usually we advice people to avoid mixing desktop environments,

... but I have tried a couple of times, and I have such a system now (Xenial, testing that things will work in 16.04 LTS).

Way back I started with Ubuntu 12.04 LTS and installed lubuntu-desktop, xubuntu-desktop and kubuntu-desktop. Things worked, but the menus were really crowded with doublets. I would *not* recommend it.

Now I am sometimes installing Xubuntu and after that lubuntu-desktop. It gives me a system that I like. I'm using the Lubuntu desktop most of the time, but there are good things under the hood and on the desktop from Xubuntu.

---

### Post by QDR06VV9 on 2016-04-01
I did this way back on 13.10 and have not tried since..[COLOR=#ff0000]**So if you proceed this way and her system breaks when logging in to unity I wont be held responsible**[/COLOR].
Not a complete answer, but you'll need to disable Global Menu first :
```
sudo -s
echo "export UBUNTU_MENUPROXY=" > /etc/X11/Xsession.d/81ubuntumenuproxy
```
Then restart your computer. 
After that, if you can delete the top panel somehow, at least you'll  keep most of your functionality. You'll need some kind of replacement  for some of the indicators, like network-manager and the session menu  for Unity at least.
If you want the Global Menus restored, simply remove that file..
```
sudo rm /etc/X11/Xsession.d/81ubuntumenuproxy
```

---

### Post by asearle on 2016-04-30
Hallo Everyone,

I found out what this was:  It was that she had accidentally created a new panel.  I was able to remove it again by right-clicking on it and selecting "delete this panel".

Many thanks for your tips.

Sorry that it was such a simple thing.

Regards,
Alan

---

