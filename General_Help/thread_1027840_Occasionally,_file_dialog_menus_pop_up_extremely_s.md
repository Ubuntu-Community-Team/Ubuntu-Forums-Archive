---
title: "Occasionally, file dialog menus pop up extremely small"
date: 2009-01-01
forum: General Help
---

### Post by sproaty on 2009-01-01
[[IMG]http://img129.imageshack.us/img129/6485/examplehy0.th.jpg[/IMG]](http://img129.imageshack.us/my.php?image=examplehy0.jpg)

This happens from time to time and is rather annoying. It doesn't seem to be limited to one particular application either, it's happened in firefox, a text editor and Amarok. 

Ubuntu 8.10 64-bit, all updates installed. Athlon X2 3800 @ 2,5GHz, 2GB DDR RAM, Nvidia 8800GT w/ 177.x drivers, Creative x-fi w/ drivers

This is 1280x1024 resolution by the way

---

### Post by Jebtrix on 2009-01-01
I noticed the same problem and my machine setup is almost identical to yours. I haven't had the time to play enough with different window managers to see if its gnome or the window manager itself (compiz, metacity, etc). :-k

---

### Post by Jebtrix on 2009-01-01
Some more digging and it turns out to be Compiz. You could enable the Window Rules compiz plugin and create a rule for Dialog window type to set a fixed size like 800x600. Not exactly the most perfect solution but it works.

---

### Post by sproaty on 2009-01-01
Thanks :)

Another thing I noticed just now, GUI-related is, for example in VLC player, hovering your mouse over the erm...video "scrollbar" pops up the current time, since the scrollbar is a fixed length. If you then just move the mouse (no need to click) across the scrollbar, the time pop-up is updated in relation to your cursor's position in the scrollbar.

This is smooth in a half-hour show if you move the mouse within 2 minutes or so of the *current* position, but as you move your mouse further away from the current time the update frequency really lags.


A similar thing happens in Firefox, scrolling with the mouse wheel in 90% of pages is silky smooth, but others have scrolling similar to what I described above, really laggy. For example, just pushing the mouse wheel up and down 5 times on a reglar site will results in the screen scrolling a few times and returning to the original position as soon as you're done moving the mouse wheel.

On other sites however, the scrolling will stop nearly 4 seconds after you stop pushing the mouse wheel, and the scrollbar is again laggy and slow here. Has anyone experienced something similar?

---

### Post by Jebtrix on 2009-01-02
Thats a known issue with Firefox on Linux and Compiz unfortunately makes it even worse. Opera scrolling doesnt suffer near as much as Firefox. I would recommend installing compiz-switch .deb from:

[http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

This way you can turn compiz on and off with one click without losing any compiz settings.

---

### Post by sproaty on 2009-01-03
Even with compiz disabled, the scrolling issue happens. I tried the scrolling after disabling compiz using that plugin to no avail :(

The scrolling is awful, whether using the up/down keyboard keys, mousewheel or the browser's scrollbar...but once again, only on certain websites. This forum is fine, but another is really slow. I did have a few FF extensions for that particular site, but disabling them had no effect

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/144216](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/144216)

this seems to describe it rather well, the last few posts link to some sites which give me noticeable problems. 

[http://www.netbreeze.com.au/test.html](http://www.netbreeze.com.au/test.html)

this runs VERY slow, 1 FPS or even less, and worst of all is that while the page is loaded, I will close the tab by right clicking on it, and it took a good 4 seconds for the tab to close. Tab closing can get extremely slow

---

