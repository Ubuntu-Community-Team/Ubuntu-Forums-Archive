---
title: "Mouse wheel scroll speed"
date: 2006-06-20
forum: Desktop Environments
---

### Post by truant on 2006-06-20
I suffer from extremely bad RSI, and the mouse wheel is just about the most pain-inducing part of my computing experience.  I'd really really like to be able to adjust the wheel scroll speed (ideally to one page per 'click') under Gnome, but all my googling and all my hacking around with various configuration files have turned up nothing.  I'm sure I managed this back in my Debian days, but I don't seem to be having any luck.

I believe the KDE people have a 'scroll speed' slider in a fancy gui thing.  I'd be more than happy to just edit a text file, if I could just find out which one to edit.

Any assistance would be greatly appreciated, thanks.

---

### Post by givré on 2006-06-20
You also have a gui for that in gnome, in prefernce i think, search a bit

---

### Post by truant on 2006-06-20
There's a Gnome gui for adjusting which buttons do what, tracking and double-click speed, but not wheel speed.

gconf has no useful-looking entries either.

---

### Post by givré on 2006-06-20
There is 3 tabs in this gui : buttons, cursors, motion.
You will be able to set the speed in the motion tab.

EDIT : oh yeah i was wrong, sorry :cool: :rolleyes:

---

### Post by Irony on 2006-06-20
I've wondered about this. In Windows I can adjust one rotation click of the wheel from moving 1 line to any amount of lines I want.

In Ubuntu one wheel mouse click rotation is 3 lines, this actually is about right for me but I assume there is some configuration file somewhere that specifies this.

---

### Post by andb on 2006-06-20
I'd be interested in knowing where the configuration is saved from the mouse config app. I have two sets of settings I want to use, "normal" and "unaccelerated" when using the qemu VM. I want to script a change in the file when I start/stop the VM. So if someone knows which file stores the sensitivity/acceleration, let us know...

---

### Post by matjaz_pirnovar on 2006-06-22
I agree,

Have searched for app for adjusting wheel speed but there doesn't seem to be any.

Any news and tips welcome...

With a tired finger...;) 

:-k

---

### Post by matjaz_pirnovar on 2006-06-22
I agree,

Have searched for app for adjusting wheel speed but there doesn't seem to be any.

Any news and tips welcome...

With a tired finger...;) 

:-k

---

### Post by truant on 2006-06-23
Some digging around a Gnome forum ([here](http://gnomesupport.org/forums/viewtopic.php?t=5355&highlight=mouse+wheel+scroll)) suggested that scroll speed was handled by gtk, and it was hard coded.  He also says that scroll speed was going to get more sensible in gtk 2.6.  But dapper ships with gtk 2.8, and that post was made in february 2004.

[this post](http://gnomesupport.org/forums/viewtopic.php?t=4150&highlight=mouse+wheel+scroll) from 2003 goes into some more detail on scrolling, and even has a patch available, but that's got to be way out of date by now.  Wading through a selection of the extremely numerous gtk release annoucements since 2.6 didn't yield any helpful information, but may well have missed it.

This shouldn't be as hard as it seems to be.  Mapping wheel clicks to page up/down can't be too tricky and would solve most page-scrolling problems, but my guess would be that other wheel uses (adjusting volume, scrolling tabs in epiphany, zooming, etc) would then break.  That would be annoying.

I'll keep looking.  Someone somewhere is bound to know something about this.  :)

---

### Post by hcgtv on 2006-07-22
I changed the mousewheel scroll in Firefox to a page at a time:

about:config

mousewheel.withnokey.action - set it to '1'

See this page for more Firefox preferences:
[http://preferential.mozdev.org/preferences.html](http://preferential.mozdev.org/preferences.html)

Now my wrist can rest a bit ;)

---

### Post by strabes on 2006-07-23
You can get one of the mouse gestures extensions for firefox, and it will let you do 'grab and drag' scrolling so you don't even have to use the scroll wheel. You can just click in the scroll wheel (it's the 3rd button) and move the cursor up and down to scroll down the entire page. This would only solve your problem in firefox i guess though.

[https://addons.mozilla.org/firefox/12/](https://addons.mozilla.org/firefox/12/)

---

### Post by ryu kun on 2006-11-14
Is there any improvement in Edgy related to this issue?

---

### Post by ryu kun on 2006-11-15
By the way, you can control your mouse wheel speed in Firefox.

Go to **about:config**
Change **mousewheel.withnokey.sysnumlines** to **false** by doubleclicking. This value sets whether the wheel's speed will be as in the system settings.
Change **mousewheel.withnokey.numlines** to a number as to how fast you like. I use 7.

---

