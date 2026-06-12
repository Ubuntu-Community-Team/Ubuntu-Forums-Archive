---
title: "Unity Desktop Issues"
date: 2012-05-24
forum: Desktop Environments
---

### Post by GuiGuy on 2012-05-24
I'm struggling with a Unity desktop (not by choice, BTW. It's someone elses system).

1) Why are there no toolbars on Nautilus?
2) Given the above, how can I set the preferences in Nautilus?
3) Why is the "Cut" menu item gone from Nautilus?
4) Why is the delete or move to trash menu item gone from Nautilus?
2) WHat happened to ALT + F2?


Thanks in advance

---

### Post by MadmanRB on 2012-05-24
for nautilus you may want to delete the hidden .nautilus folder, I had this issue myself when going from 11.04 to 11.10

---

### Post by GuiGuy on 2012-05-24
> **MadmanRB said:**
> for nautilus you may want to delete the hidden .nautilus folder, I had this issue myself when going from 11.04 to 11.10

That's what I thought, but there is no such folder, hidden or otherwise.

I just noticed that other applications, i.e. firefox, terminal etc all have the toolbar menus missing as well.

:(

We were about to image three PCs with with ubuntu but I think I'll try and talk them into mint.

---

### Post by typhoon_tip on 2012-05-24
Try and run

```
unity --reset
```

Beware that you may have some errors shown, but that's normal. Do not close the terminal after running that command, but once Unity is back, simply logoff/login again.

---

### Post by kansasnoob on 2012-05-25
> **GuiGuy said:**
> That's what I thought, but there is no such folder, hidden or otherwise.

I just noticed that other applications, i.e. firefox, terminal etc all have the toolbar menus missing as well.

:(

We were about to image three PCs with with ubuntu but I think I'll try and talk them into mint.

I'm guessing you simply don't understand how the "global menus" work. The "toolbars" only appear when you hover the mouse pointer over the top panel.

I'm using Lubuntu right now so let me log into an Ubuntu install and try to display a couple of screenshots :)

---

### Post by kansasnoob on 2012-05-25
Here's two screenshots. In the first you'll see that I show no toolbar options but in the second you'll see that I hovered the mouse pointer over the top panel and the typical options appear:

[ATTACH]218675[/ATTACH]

[ATTACH]218676[/ATTACH]

Additionally you can revert to a classic DE if you so wish:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

BTW: That "system problem" warning is only because I've been using that install for SRU testing.

---

### Post by GuiGuy on 2012-05-25
> **kansasnoob said:**
> I'm guessing you simply don't understand how the "global menus" work. The "toolbars" only appear when you hover the mouse pointer over the top panel.

Yes I do and no they don't. That's been my problem. 

Anyway, I've solved by another way

---

### Post by GuiGuy on 2012-05-25
Thanks for all the replies people. But enough's enough. We've gone all minty as a solution. I feel much better now... :)

---

