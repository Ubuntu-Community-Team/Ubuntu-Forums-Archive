---
title: "lxpanel not at the edge of screen"
date: 2012-07-13
forum: Desktop Environments
---

### Post by smitty96 on 2012-07-13
When I log into Lubuntu now, the panel isn't all the way at the top of the screen. There's a screenshot [here.]("http://db.tt/cVDP9L7r") This has been happening since I started using multiple monitors on my system, but it happens every time I login, even if the second monitor is not plugged in/turned off.
I can get it back to the top by setting it to the bottom edge and then the top again, but I have to this each time I login. Any idea why this would happen/how I can fix it?

---

### Post by Guilden_NL on 2012-07-13
It's getting late here, and I've had a long day. So I won't be able to offer troubleshooting tips, but can point you here: [http://pclosmag.com/html/Issues/201010/page07.html]("http://pclosmag.com/html/Issues/201010/page07.html") where there are plenty of details covering how to configure LXPanel.

Good luck!

---

### Post by smitty96 on 2012-07-13
Thanks for the link, but it doesn't look like my problem is really addressed in there. The panel *is* set to display at the top, it's just not all the way there for some reason. It's getting late here as well, maybe someone in a different time zone will find something before morning :p

---

### Post by puntigamer on 2012-07-13
Hi,  
check out this website: [http://wiki.lxde.org/en/LXPanel](http://wiki.lxde.org/en/LXPanel) 
Search your config file (in ~/.config/lxpanel/LXDE) for the line like this:

```
margin=0       # margin: margin to the edge of the whole screen  
```maybe there could be some mistake, what makes your panel act funny :)

---

### Post by ankspo71 on 2012-07-14
If this is caused by lxpanel starting too quickly then this link should help: 

Delay lxpanel autostart in Lubuntu
[http://ubuntuforums.org/showthread.php?t=2024713](http://ubuntuforums.org/showthread.php?t=2024713)

---

### Post by smitty96 on 2012-07-22
Unfortunately, I tried both of those and no success :/ . That last one gave me an idea, and when starting lxpanel with the Lubuntu profile, even after all other programs are loaded, it does not go completely to the top of the screen. It actually looks as if the space being reserved for the panel is actually being avoided by the panel itself :confused:
EDIT: My own post just helped me! Woo! I just had to click the "make window managers treat panel as dock" option and voila, it places itself correctly now. Thanks everyone for your suggestions, they all at least helped me understand LXDE a bit better.

---

