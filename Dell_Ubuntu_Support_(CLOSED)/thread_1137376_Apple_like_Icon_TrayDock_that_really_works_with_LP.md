---
title: "Apple like Icon Tray/Dock that really works with LPIA Ubuntu?"
date: 2009-04-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vickoxy on 2009-04-25
Hi,
i saw that many users have those Icon trays similar to Apple icon tray. I installed couple of months ago Awant Window Manager but it didn´t work. Does anyone knows any simple Apple like/similar Dock/Tray that works under Ubuntu 8.04 LPIA?

---

### Post by jasreca on 2009-04-25
what didn't work exactly?

I think you have to have compiz enabled for awn to show...

---

### Post by vickoxy on 2009-04-25
> **jasreca said:**
> what didn't work exactly?

I think you have to have compiz enabled for awn to show...

That was it, i think. But i want dome dock in metacity rather than in compiz (too slowly for me). Is there any stable alternative (that i can install from synaptic)?

---

### Post by jasreca on 2009-04-25
well if compiz slows the machine down, I suppose you don't want to give it any extra load, so if I were you, I'd give up on rendering all those fancy icons altogether... Maybe just have the old panel and put the icons/shortcuts on it? But I suppose you still want it to look fancy?

I don't know. Maybe someone else has an idea...

---

### Post by vickoxy on 2009-04-25
> **jasreca said:**
> well if compiz slows the machine down, I suppose you don't want to give it any extra load, so if I were you, I'd give up on rendering all those fancy icons altogether... Maybe just have the old panel and put the icons/shortcuts on it? But I suppose you still want it to look fancy?

I don't know. Maybe someone else has an idea...

:) No, i was used to such a bar on macbook-and i really don´t need it with dell mini 9, but when i plug in external monitor then i have plenty room for such a dock. But i want something simple because of the reason you mentioned.

---

### Post by vickoxy on 2009-04-25
I found here something on compositing metacity, which enables awn and other effects. I don´t even know what that means, but should i try it?:) Or i can really mess up my mini?

[http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/](http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/)

---

### Post by vickoxy on 2009-04-25
So i noticed that metacity does not support most of the docks...
If anyone has any suggestions,,,

---

### Post by vickoxy on 2009-04-26
I set up one panel and increase the icons size-it is doing its job just fine-still i have to aski if these 2 things can be adjusted:

1)can it be so transparent that i can see dekstop icons behind them (i made it transparent, but only Desktop picture is to see - the folders on desktop are not)

2) i would like the panel  totally to disapear (only to opened when i move cursor to the bottom of desktop)-but there are always 2-3 pixels of panels which are visable.

This are not big issues, but... 

Anyway, if someone has some suggestion which dock bar works under metacity and LPIA Ubuntu 8.04...

---

### Post by vickoxy on 2009-04-26
Unfotunately, when i choose to reduce panel size where are my Applications Icons, everything works just well as long i don plug external monitor. But when i do that, panel goes up and everythig is messed up. Does anyone knows, how to put panel beneath/down with external monitor and with that adjustable reduced size?

---

### Post by vickoxy on 2009-04-26
Here is the picture:

---

### Post by jasreca on 2009-04-26
Hm... well, panel properties/orientation/bottom? :)
And what gets messed up? From what I can see, looks OK, just need to change panel orientation to bottom... Or not? :P

P.S.
Grüße aus Zagreb :) 
Ich sehe jetzt aber, dass dein Gruss in der Zwischenzeit verschwunden ist... :)

---

### Post by vickoxy on 2009-04-26
Yes it looks fine, but it supposed to be at bottom (this picture was made wtih external display plugged in-means that after plugging the monitor dock goes up-and it acts weird-glitches, buggy...). When i unplugg the display, panel is at the bottom, working just fine...)-these problems are there only when the panel size is adjusted/shorter-when it is full sized then all work just fine.

I post similar thread here-i am open to any suggestions:

[http://ubuntuforums.org/showthread.php?t=1138460](http://ubuntuforums.org/showthread.php?t=1138460)

---

### Post by vickoxy on 2009-04-27
Ok, i solved my problem with Panel-i put it on the left side, so it is shown properly after plugging in/unplugging the external display. I also get rid of those extra pixels that usually stay visasble, although the option "hide" activated is (have to adjust "monitor" section-carefully read following instructions-your Ubuntu may freezes sometimes if you choose some numbers-i think 5 or 6, but i am not sure: [http://ubuntuforums.org/showthread.php?t=230300](http://ubuntuforums.org/showthread.php?t=230300))

This is really elegant solution for Matacity/LPIA Ubuntu. If you install KoolDock/AWN the system will not be so smooth...

---

### Post by vickoxy on 2009-04-27
Sorry for putting these post on several threads, but maybe others will find it usable. 

I succeeded to make KoolDock working just fine in Dell´s Ubuntu 8.04 (lpia).
First: from synaptic you can download only KoolDock 0.3-no good...it won´t work. 

1) Find then on line KoolDock 0.4.6. and download it
2) install KDEbase (it will install 34 Packages with more than 70 MB... i didn´t notice any change in my system-hope just that this downloads are not fatal)
[http://lists.kde.org/?l=kde-announce-apps&m=119053945506482&w=2](http://lists.kde.org/?l=kde-announce-apps&m=119053945506482&w=2)
3) Doobleclick on your KoolDock (you can previously install from synaptic 0.3 if you want....) and installation will go automatically

So, that was it. Panel and KoolDock are fastest Launchers for Metacity LPIA Ubuntu 8.04-you don´t have to activate compositing metacity. There are some issues-fonts looks ugly-so better do not show them. But the panel is quick, installation of new apps is easy (just drag and drop), and transparency works fine (sometimes there are some glitches...but nothing serious).

P.S. I didn´t figure how to add folders and documents on KoolDock, so if anyone find solution...

---

### Post by jasreca on 2009-05-03
Maybe this could be of some help, just ran into it - it's called Cairo Dock and apparently can be run without a composite winmanager...

[https://help.ubuntu.com/community/CairoDock]("https://help.ubuntu.com/community/CairoDock")

---

### Post by vickoxy on 2009-05-03
> **jasreca said:**
> Maybe this could be of some help, just ran into it - it's called Cairo Dock and apparently can be run without a composite winmanager...

[https://help.ubuntu.com/community/CairoDock]("https://help.ubuntu.com/community/CairoDock")

Hi, i just test it-it works almost perfectly-have some issues with plug ins (probably because i installed the latest version):
[http://ubuntuforums.org/showthread.php?t=1145316](http://ubuntuforums.org/showthread.php?t=1145316)

But, also whitout them, cairo-dock is amazing...

---

