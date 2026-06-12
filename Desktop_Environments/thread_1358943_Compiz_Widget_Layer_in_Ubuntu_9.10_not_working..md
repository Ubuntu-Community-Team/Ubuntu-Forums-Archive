---
title: "Compiz Widget Layer in Ubuntu 9.10 not working."
date: 2009-12-19
forum: Desktop Environments
---

### Post by vehemence on 2009-12-19
Hi guys, first time poster here- I've always found a lot of answers so I needn't make another post of something someone has already solved.
But anyway, here's my problem:

I've recently "themed up" my Ubuntu to make it look very similar to Mac OS X. This is all well and good, it looks fine, and the dock works etc.
I've installed Screenlets and CCSM, enabling the options I'm meant to, but when I hit F9 the layer does not show.
The screenlets work fine on my desktop, but when I use "treat as widget" it doesn't disappear from the desktop, nor does it make the layer show up if I press F9 again.

I've checked the hotkey is right- it is.

Any help would be greatly appreciated :)

---

### Post by redmistpete on 2010-01-14
> **vehemence said:**
> Hi guys, first time poster here- I've always found a lot of answers so I needn't make another post of something someone has already solved.
But anyway, here's my problem:

I've recently "themed up" my Ubuntu to make it look very similar to Mac OS X. This is all well and good, it looks fine, and the dock works etc.
I've installed Screenlets and CCSM, enabling the options I'm meant to, but when I hit F9 the layer does not show.
The screenlets work fine on my desktop, but when I use "treat as widget" it doesn't disappear from the desktop, nor does it make the layer show up if I press F9 again.

I've checked the hotkey is right- it is.

Any help would be greatly appreciated :)

1- Make sure that widget layer is enabled (put a tick in the box on CCSM)
2- In the settings, set brightness to 50% and then hit F9 to test if widget layer really is working. Otherwise, Widget layer itself doesn't do anything noticeable until you start assigning things to the layer.
3- Assuming that the screen now fades when you hit F9 (proving that the layer is working), you must "add" your widgets/desklets/gadgets/panels and whatever you want on the layer USING CCSM. You can add all sorts of things with filters such as class/name/type etc. Adding via "Treat as Widget" wont work if you're running CCSM because CCSM requires you to tell it which are the widgets. 
4- once you've added your widgets and they work as required you can set the brightness back to whatever you like.

Hope this helps

Edit - screenlets is great - when you click "Install" go to the drop down list and click "convert web widget" you can then add widgets from google gatgets and a wealth of other screenlets type apps which are (to be fair) a lot better and there are 1000's of them!

Also MACish is "GLX-Dock" which is great for 9.10 in the ubuntu software centre

---

### Post by sailorboy on 2010-02-01
Found this forum very helpful, I also had no apparent F9 key to toggle the widget layer and wondered where the screenlets were going. Turns out, (I'd forgotten)- this keyboard has a "F-Lock" button to toggle the multifunction keys. Pressing 'shift' alone doesn't do it.
 Now F9 works, but will reset on reboot.
 I presume one could find a way to enable this on startup or login if the other shortcuts were not needed, but 'edgepoint' works OK for me.
 Actually, this 6yo dell on karmic ROCKS!

---

