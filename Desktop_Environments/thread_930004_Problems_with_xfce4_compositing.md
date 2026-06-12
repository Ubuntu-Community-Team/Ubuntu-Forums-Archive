---
title: "Problems with xfce4 compositing"
date: 2008-09-25
forum: Desktop Environments
---

### Post by crimesaucer on 2008-09-25
I have a question for xfce4 users..... 


Over the last 2 years of using xfce4, I noticed that once Firefox 3 started using the Linux theme, Firefox does a weird thing with the gtk when it opens and closes. 


It sometimes opens as 3 boxes, just like the "startx" does before you install a desktop environment to see if your xorg is configured correctly..... (like the 3 different size terminals and the mini clock after you run the command "startx" while in a tty console).


I also notice xfce4 has a weird "sideways" breakage with the right click menu and even on the webpages when I scroll.... (like a diagonal tearing). The menu will drop down with a diagonal mess that quickly fixes it's self and then stays fixed. When scrolling down a long web page, everything looks good and feels normal and then there is a quick breakage in the middle of the page (also diagonal). It's like a BIG version of the menu.   


It's done that on i386 xubuntu, i686 Arch, and Arch x86_64. All of these with xfce4 and compositing. 


It also DOESN'T do this with gnome metacity (and metacity-compositing) or compiz-fusion.


I prefer xfce4 with compositing to compiz-fusion or metacity, but the diagonal tearing thing when scrolling web-pages is a deal breaker for me. So I end up on xfce4 with compiz-fusion.


Does anybody else get these weird errors?

---

### Post by crimesaucer on 2008-09-25
Even when using compiz-fusion, this is what firefox looks like when it opens to my home page:

[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-7-1.png[/IMG]


.... this is the diagonal tearing that happens on the xfce4 menu also.

---

### Post by crimesaucer on 2008-09-26
..... so nobody else get's an ugly firefox when it opens with compositing on??????


Only compositing does this. (xfce4 or compiz)

---

### Post by jdarias on 2008-10-02
Yea i've noticed this too. When i wanna rest from it, i turn off composition.
I'm currently looking to change xfwm for metacity to see if this soves it, and also to get gimp 2.6

---

### Post by crimesaucer on 2008-10-03
> **jdarias said:**
> Yea i've noticed this too. When i wanna rest from it, i turn off composition.
I'm currently looking to change xfwm for metacity to see if this soves it, and also to get gimp 2.6


I slightly fixed this.... what I did was I logged into my xfwm4 window manager and turned the xfce4 compositing off while using compiz-fusion compositing.

---

