---
title: "Change virtual screen size without restarting?"
date: 2009-02-12
forum: General Help
---

### Post by MattPhillips on 2009-02-12
Hello,

xrandr is great but it doesn't appear to allow you to change your virtual screen size.  The only way I know how to do that is to edit xorg.conf and restart.  Is there a way to do it without having to restart?  Thank you!

Best,
Matt

---

### Post by Thelasko on 2009-02-12
Not that I'm aware of.  Keep in mind, once you set the virtual screen size, you shouldn't have to change it again.

[Here's some documentation.]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")  If you make your virtual screen size larger than 2048x2048 you will lose direct rendering on Intel graphics cards.  Smaller virtual screen sizes user fewer resources, and therefore increase performance.

---

### Post by MattPhillips on 2009-02-12
Hi Thelasko,

Thanks for getting back to me--

> Keep in mind, once you set the virtual screen size, you shouldn't have to change it again.

Actually, I need a smaller virtual screen for getting direct rendering, and a larger virtual screen to get full resolution from my monitors.  So if there was a way to do this without restarting it would be really helpful.  Thanks anyway!

Best,
Matt

---

### Post by Thelasko on 2009-02-12
> **MattPhillips said:**
> Actually, I need a smaller virtual screen for getting direct rendering, and a larger virtual screen to get full resolution from my monitors.  So if there was a way to do this without restarting it would be really helpful.

Did you try arranging them (virtually, not in real life)[ vertically]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#the_Virtual_screen")?

---

### Post by MattPhillips on 2009-02-12
Hi Thelasko,

Rearranging them vertically would indeed fit them within the 2048x2048 window, but the disconnect between the physical and virtual relationships of the monitors would be too distracting--e.g. I naturally move the cursor to the left to bring it back to the laptop monitor, but I would need to move it down instead, etc.  Thanks for the suggestion though.

Best,
Matt

---

### Post by schweigi42 on 2011-01-16
Even so this thread is already a little bit out of date, I'd like to give my two cents...

> Rearranging them vertically would indeed fit them within the 2048x2048 window, but the disconnect between the physical and virtual relationships of the monitors would be too distracting

With my 'big' computer at work I use the two monitors side by side - so I have to move left-right to change the mouse cursor between monitors.
But my notebook at home has the 2048x2048 limitation so I stack the notebook display and the external monitor logically on top of each other. Both have a resolution of 1400x1050. Therefore I have to additionally let them overlap a little bit - I do this with 'xrandr --output VGA1 --auto --pos 0x998'. Looks weird on the first sight but you get used to it faster than you might think - for both - that you see some border of the windows on both screens as well as moving to the other screen means moving the mouse up or down...
 
bernhard

PS.: For me it was the only way to use both monitors with my notebook and still have hardware-accelerated graphic output...

---

