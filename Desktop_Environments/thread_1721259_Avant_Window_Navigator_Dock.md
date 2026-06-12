---
title: "Avant Window Navigator Dock"
date: 2011-04-04
forum: Desktop Environments
---

### Post by HeroKing on 2011-04-04
well, i just got this downloaded and i kinda like it. haven't customized it with apps yet, but i'll get to that later. right now i was wondering if there was any way i can set it to panel mode with only my desktop, yet still have my windows overlapping it.

---

### Post by Frogs Hair on 2011-04-04
Right click the dock and select dock preferences and you will find settings to extend the dock and much more . Just explore the drop down menus.

---

### Post by HeroKing on 2011-04-04
i already know that. what i mean is set it to Panel Mode and still have any active windows access the full width of my desktop. as far as i can tell, it doesn't have that option

---

### Post by Frogs Hair on 2011-04-04
The intell hide will option hide the dock and allow an active window to overlap it and the dock will appear when you hover in the dock area. Is this closer to what you are looking for or am I misunderstanding.

---

### Post by HeroKing on 2011-04-04
well, what i want is basically this. when it's in Panel Mode, it basically locks onto your desktop, moving your desktop icons to the side so they don't appear under it (i have it set to the left side of the screen). but when it does that, it also locks out any active windows from overlapping it, which i want them to do. i'm basically trying to recreate my desktop to look like this envronment, and having the dock set to the max 100 pixels is a part of it. i'd have my own screenshot, but i'm at a public computer right now
 
[http://farm4.static.flickr.com/3257/2334934107_cc0b1d7f33.jpg](http://farm4.static.flickr.com/3257/2334934107_cc0b1d7f33.jpg)

---

### Post by Krytarik on 2011-04-04
Then the "panel mode" is exactly what you *don't* want! I believe there is also an option to expand the panel, but I don't have it installed currently, so I can't check.

---

### Post by shafin on 2011-04-04
In AWN settings, in the Preferences tab, Choose 'Always Visible' as Behavior instead of 'Panel', and Tick "Expand Panel". Then you will have your windows overlapping the stretched panel. However, you'll hae to shove the desktop icons away yourself.

---

### Post by Copper Bezel on 2011-04-04
Actually, he'd want "Dodge Window." "Always Visible" does what it says on the box. 

So just to summarize, you want windows to cover the panel, but you don't want icons getting lost under it; that seems quite reasonable, but I don't know if it'll work easily. I think the best method might be to see what you could do with a Folderview Screenlet instead of using the desktop for icons - if you can set it to be entirely transparent and make it the size of the desktop area you want, that should do the trick. I haven't really played with it, though.

If you want the desktop moved over, you'll have to do that by manually editing the image - AWN doesn't do that.

Good luck - that's a very pretty mockup!

Edit: No dice with Folderview - you can make it look exactly like desktop icons, but it's fairly useless in practice.

I think this is a failing of the way that AWN is implemented. I mean, most DEs can handle panels, but AWN doesn't behave anything like an ordinary panel except when it's in panel mode. I wonder if it's all one setting, that the desktop for icons is the same as the desktop for windows, so there's just no framework for AWN to call on here. (But then, I don't actually know how panels work in that sense.)

---

### Post by Krytarik on 2011-04-04
> **Copper Bezel said:**
> (But then, I don't actually know how panels work in that sense.)
Actually, they don't. What the OP wants is also not possible with the usual panels.

---

### Post by Copper Bezel on 2011-04-04
I guess I mean I don't know how any panel or dock - Gnome Panel, AWN, Cairo-Dock, Docky, or even XFCE's panel or any of the other lightweights - reorganizes x-nautilus-desktop and changes the available area for maximized windows. I'm curious because I don't know whether those are two separate values or whether the desktop icon space only always fills the available area for maximized windows. If they're separate values, then what he's looking for would be possible for AWN to implement and would be worth making a suggestion for; the panel never disappears unless occluded by another window, so the icons *should* ideally remain displaced even when Intellihide is activated.

---

### Post by Krytarik on 2011-04-04
I guess that both the icon space and maximized windows are affected by the same variables. This earlier thread, we both were taking part in, delivers further evidence for that theory:
[http://ubuntuforums.org/showthread.php?t=1714459](http://ubuntuforums.org/showthread.php?t=1714459)

---

### Post by Copper Bezel on 2011-04-04
That seems likely, yeah. Good point.

---

### Post by HeroKing on 2011-04-04
thanks for the help, guys. i suppose i can try and take a look at other dock programs and see if they give what i would hope i want. and since i'm on my laptop, i can post a screenshot of what i currently have running. aside from the dock issue and the option i want for the taskbar, i'm very close to recreating the desktop environment based on the game i took it from.

[http://i55.tinypic.com/28jmnk.png](http://i55.tinypic.com/28jmnk.png)

---

### Post by Copper Bezel on 2011-04-04
Looking good! Good luck with finding a more suitable dock.

This [icon theme]("http://gnome-look.org/content/show.php/Clarity?content=135654") looks close to what you're trying to do, too (although they're not glowy, sadly.)

---

### Post by HeroKing on 2011-04-04
well, i'm not too concerned about an icon pack because in the original version, the icons on the dock were 3D and constantly rotated in a horizontal direction (whereas Avant does a vertical when it's clicked). i actually saw a very near perfect replica of it, but it was for Win7, which i'm not gonna bother trying since i can't get it lol. i tried Docky just now, and for some reason, it made my laptop crash when it was active along with my startup screenlet >.<

i actually started this when i saw someone else make it and posted a screenshot on deviantart here - [http://dubkatz.deviantart.com/art/dubHack-Za-Warudo-quot-The-World-quot-40576949](http://dubkatz.deviantart.com/art/dubHack-Za-Warudo-quot-The-World-quot-40576949)

only now i see he has 2 docks active, along with his custom icons that are available on the page

---

