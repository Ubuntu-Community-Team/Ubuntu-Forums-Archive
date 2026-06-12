---
title: "Old Problem with Firefox, just upgraded to 8.10"
date: 2008-12-04
forum: General Help
---

### Post by Dunover on 2008-12-04
My Minimize, maximize and close icons missing? I was doing some browsing today and the icons on the above right corner of the firefox window were gone, and the top of the firefox bar is so high I cannot move it. There is no way that I can find to minimiz it anywhere and to access other programs I have to use alt+tab. How did I break it or better yet how do I fix it? Thanks!
Corisa

---

### Post by ashwin_mood on 2008-12-04
yeah , i had a same problem when i freshly installed ubuntu 8.10.
 can anyone help me please....?

---

### Post by T_W on 2008-12-04
Alt + Drag should allow you to move the window even if you cannot access the title bar.

The title bar may just be hidden under the panel.

---

### Post by Shwefty on 2008-12-04
I hear F11 does wonders :).

If Firefox is in full-screen, it'll take it out of it.

---

### Post by Dunover on 2008-12-04
Thanks..for the help... alt drag just does nothing..... f11 just makes it full screen?  Is this a bug with firefox or ubunut??
Cori

---

### Post by philinux on 2008-12-04
> **Dunover said:**
> Thanks..for the help... alt drag just does nothing..... f11 just makes it full screen?  Is this a bug with firefox or ubunut??
Cori

If you're running compiz check the "window decorator". Untick it then tick it.

---

### Post by Shwefty on 2008-12-04
I don't know...I'm still trying to visualize the problem.  One more try, do you see your Gnome taskbar?  If you do, right-click on the Firefox bar and select "Resize".  Maybe that'll work?

And double check on Philinux's post...that was the next stop in the solution train! :)

---

### Post by Dunover on 2008-12-04
> If you're running compiz check the "window decorator". Untick it then tick it.

What is compiz?  No I cannot get to the tack bar top bottom or on the side... the only way to get out is to alt tab, or close via File

Corisa

---

### Post by Shwefty on 2008-12-05
Compiz is your visualization manager.  To get CompizConfig Settings Manager, go to Add/Remove Programs, search for "ccsm".  The first/only result should be Advanced Desktop Effects Settings (ccsm).  Select this option for download and hit okay.  Even if his idea doesn't work...you'll be glad you have this settings manager, so all is well!

Then, once installed, go to System -> Preferences -> CompizConfig Settings Manager.  Under the Effects heading, uncheck "Window Decoration", pause for changes to take place, recheck "Window Decoration", pause for changes to take place.  Hopefully that'll take care of it.  Check out all the awesome options in there too like Opacify under Accessibility.

---

### Post by Dreamer Zero on 2008-12-05
> **philinux said:**
> If you're running compiz check the "window decorator". Untick it then tick it.

thank you, this fixed mine. or did it? will it start again after i reboot? because it is getting on my nerves having to do the F11 thing everything i load a work related webpage.

thanks again.

---

### Post by Shwefty on 2008-12-05
Well, reboot then find out! :)

I think it's a one-time fix all though.

---

### Post by philinux on 2008-12-05
Compiz has glitches now and again. I've had to perform this trick a few times. It sticks with a reboot though.

---

