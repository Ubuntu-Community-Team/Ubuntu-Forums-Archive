---
title: "Emerald themes, not appliying completely?"
date: 2009-12-17
forum: Desktop Environments
---

### Post by jack0 on 2009-12-17
Well as many of you,i have seen amazing screenshots of emerald themes.

Like the one in these picts:

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/Desktop.png[/IMG]
[IMG]http://yaro.marupa.net/gallery/screenshot108.png[/IMG]

(notice the panels transparencies)
(this pictures are what i want to get)

(stolen images).


The thing is, i ony get this.

(this is how MY destop looks with emerald running)

[IMG]http://i36.photobucket.com/albums/e35/6u0W/Pantallazo.png[/IMG]


Is this because this is ubuntu and not kubuntu?
I mean, because it uses gnome?
 

In that picture i changed top and bottom bars to use solid color, otherwise those would look gray too.



How do i get those nice transparencies?


Also, the main theme (panel colors, window background.. seems to be still controlled by metacity (you must pick them in appearance), is this the way it works normally?



And, is there a theme pack , as it used to be in emerald-themes package? (btw that package has disappeared from the web)

thanks will check this later

---

### Post by doas777 on 2009-12-17
just to clarify, is emerald doing anything? if not, try running 
```
emerald --replace
```. if that fixes your issue, add it to your startup applications.

---

### Post by jack0 on 2009-12-17
> **doas777 said:**
> just to clarify, is emerald doing anything? if not, try running 
```
emerald --replace
```. if that fixes your issue, add it to your startup applications.

Yes, Emerald is loading.

and it does work, switch themes and etc.

But what i dont have is that beautiful transparencies.

how do i enable them?

---

### Post by doas777 on 2009-12-17
well, the transparent terminal is controled via the terminals edit menu, under profiles.
the rest can be done with the compiz config settings manager (ccsm).

---

### Post by jack0 on 2009-12-17
Well that was better, thanks.

Indeed changing that setting in the profiles config, makes the terminal transparent.

I guess you are suggesting i enable the opacity saturation etc setting in ccmp, and that way i can use alt+wheel to set the transparency of the windows.

well that would work, but i dont want to make the hole window transparent, i just want some parts of it (the ones that contain the buttons like up and back) to become little transparent.

Like in the blue picture, that you can see the lines of the desktop wallpaper through that part of the window.

I would like to copy and make the drop down "applications" menu transparent too.

ive searched the forums and some say i must install some "murrine" tring that adds rgba support ..?

[http://ubuntuforums.org/showthread.php?t=1325661&highlight=gnome+transparency&page=2](http://ubuntuforums.org/showthread.php?t=1325661&highlight=gnome+transparency&page=2)

Is that really/still needed?

Some others talked about another program... some settings.. about gnome... lost that thread.

Yet some ppl just talk about installing compiz and emerald.

will search better tomorrow, its late now, but if you can point me in the right direction, its appreciated.

---

