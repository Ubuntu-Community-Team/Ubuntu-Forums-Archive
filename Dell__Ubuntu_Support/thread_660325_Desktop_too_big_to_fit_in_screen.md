---
title: "Desktop too big to fit in screen"
date: 2008-01-06
forum: Dell  Ubuntu Support
---

### Post by mra122 on 2008-01-06
Hi,
I look at all the other posts that are the same  as my problem...
But none of them helped, so I'm posting this one...

So hear goes nothing, I have a dell latitude d610, with an SXGA screen upto 1400x1050, which worked perfectly fine until I installed the new ATI 7.12 driver (I have radeon x300), and right after the installation the desktop does no longer fit on the screen,
but if I move the mouse over to the edges of the screen I can see the other part of my desktop.
I tried changing the resolution, and it does help, but I want to work at 1400x1050 like before...what can I do..?
I also tried changing the screen under: system->administration->screens and graphics, to something else, but the problem remains...

Please help me...I'm desperate!!!

Again, I just want to say that it all happened after installing the new ATI 7.12 driver...
Oh, and my problem is same as described in this thread, but there's no solution there either:
[http://ubuntuforums.org/archive/index.php/t-510880.html](http://ubuntuforums.org/archive/index.php/t-510880.html)


Thanks everyone for helping,

mra122.

---

### Post by RebounD11 on 2008-01-06
I have that problem after I exit Counter-Strike :D

I can usually fix it by changing the resolution and applying the settings, and then go back to my desired resolution. I change the resolutions from Catalyst Control Center not from screen resolution changer in the System menus.

Sometimes it persists until I hit Ctrl+Alt+Backspace and login again.

Hope this helps.

PS: I recommend going back to 7.11 drivers. They worked better for me.

---

### Post by Bllasae on 2008-01-06
Yeah, just change the resolution, or if you're using a desktop, press the menu button on the monitor, and then find the width and make it shorter(Or length, depends on what the problem was.)

---

### Post by mra122 on 2008-01-07
But the problem is that it all worked before....
why did it stop working after installing the new driver :-(
I hate ATI!!!!!
Any other suggestions besides the ones already posted?
Maybe modifying something in the xorg.conf file?

Thanks everyine for posting :)


mra122.

---

### Post by Tarmael on 2008-01-07
Could we get a screen shot of this?

For two reasons:
1) so we can see the problem.
2) because it sounds cool. (In a, it's a big problem sorta way)

---

### Post by mra122 on 2008-01-08
There's a problem with posting a screenshot...cause when I make a screenshot it captures the entire screen and you can't see the edges that's missing...
Bummer :-(

HELP!!!

---

### Post by mra122 on 2008-01-10
I solved the problem...
I had to edit the screen section in xorg.conf....because for some reason the 7.12 driver causes problems with certain resolutions...
If anyone wants to know how I fixed it, so I googled "dell 1400x1050 xorg.conf" and just copied the screen section from one the the first results, and that fuxed the problem...
If anyone has any questions about this feel free to send me a private message :-)


mra122.

---

