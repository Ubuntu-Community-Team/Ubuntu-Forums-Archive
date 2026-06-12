---
title: "Tilda doesn't get focus when running with Beryl"
date: 2007-02-05
forum: Desktop Environments
---

### Post by madjo on 2007-02-05
I'm running Feisty (since yesterday). And it looks really great, especially with Beryl installed.

Beryl itself runs fine (aside from a few crashes, but those are reported), it's just that it has a weird effect on Tilda.
Tilda is visible, and it works, it just doesn't get focus automatically. I have to click inside the tilda window to get focus. (or alt-tab to it)

Does anyone know what I can do about it?

When I run in Metacity, tilda gets focus immediately.

Also 'always on top' doesn't seem to work all the time.

---

### Post by madjo on 2007-02-06
*bump* :)
Does anyone have any idea?

---

### Post by originofstorms on 2007-02-08
There may be a less heavy-handed way of doing this, but I got tilda to grab focus by visiting the General Options section in the beryl manager, and setting Level of Focus Stealing Prevention to None. It remains to be seen if this was a bad idea.

---

### Post by dr_d on 2007-02-28
getting the same problem -- it doesn't really bother me that much though.

haven't tried setting fsp to none --- i'll take your word that it works :)

---

### Post by asantainnasa on 2007-03-03
same problem here
and also, the window isn't truely transparent when i set it to be in options, it only mimics my desktop background. So if i'm running tilda infront of other programs, it looks really bad, since it's like a portion of the desktop is showing
help? =/

---

### Post by dr_d on 2007-03-04
well i decided that it *does* bother me, and i tried the fix and can confirm that it works with no noticeable side-effects.

as for transparency, it works if you use beryl itself to set the transparency instead of letting tilda manage it..

drop down your tilda, hover the mouse anywhere over the window, hold down alt, and roll your mouse wheel :) 

works great -- only problem it you have to do it each time you boot.

---

### Post by asantainnasa on 2007-03-04
thanks!
i'll try doing that
cuz i didn't know you could bring the menu up that way
=]

---

### Post by asantainnasa on 2007-03-04
=/ my emerald manager/ window decorator crashes when i try alt + right click

---

### Post by Gadren on 2007-04-21
I hope I'm not breaking any bumping rules here, but I wanted to pop in and say thank you!  This is precisely what I needed -- now I can use the terminal so easily...

---

### Post by kungfooguru on 2007-04-23
Yes, you have to turn off 'prevent focus stealing' in the window manager. This is a problem in beryl and KDE at least, they turn it on by default. 

Other window managers, xfwm, metacity, etc are nice enough not to have this feature turned on. There is no work around since the point of 'prevent focus stealing' is to not allow me to have Tilda do what it should do. Very annoying.

Tristan

---

### Post by GoPool on 2007-05-02
I may have the same problem using compiz on Feisty 7.04. What must I do to get the active window to move to the front of all other windows, apart from click the title bar. Thanks you.

---

### Post by starcraft.man on 2007-05-26
Yay for this old thread, I just got tilda in and have been using it a lot and was getting just a bit frustrated with it not popping on top of my active window. 

Score one for the forums :).

---

### Post by EnthropyinAction on 2007-09-26
Sorry no info on the compiz problem, but thank you for the fix with Tilda.  It always amazes me that if I have a problem, someone's already complained about it and gotten a fix  :p

---

### Post by sundance2007 on 2007-12-08
> **kungfooguru said:**
> Yes, you have to turn off 'prevent focus stealing' in the window manager.
Tristan

OK, I'm new and I'm not sure where I find this window mang. to do this. Where will I find it? I looked  > system > prefs > window and I found Windows prefs. but the only items to change were:

Window selection
Titlebar action
Movement Key

nothing about focus.

Also under visual effects when I try to enable them I get a message saying they can not be enabled. Could this be due to my video card not having enough horse power?

(Ubuntu 7.10)

Thanks

---

