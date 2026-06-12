---
title: "No panel."
date: 2008-07-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Faryshta on 2008-07-17
Hi I am using Hardy and I can't see the panels of my Gnome neither the one upside or downside.

Someone knows how to change the panel properties (like width, color, etc.) using the console?

I tried command
gnome-control-center

Appears a window very complete but the panels are not posible to modify there.
Thanks.

---

### Post by PinkFloyd102489 on 2008-07-17
Hit Alt+F2 and enter "gnome-panel" into the box to get your panel back.

---

### Post by raydar on 2008-07-17
I run gnome-panel and get a message that it's not installed. Is it supposed to be in /usr/bin like a gnome-panel-screenshot is?

I'm running Hardy Ubuntu Studio, and my panels disappeared after the recent update and after I un-installed the only Evolution package that came installed in 'Studio, which was evolution-data-server (one of those to be updated; I was about to try Thunderbird again, so I thought why update Evolution?).

I had trouble getting a terminal window, having no menu-bearing panels and because strangely, ALT+F2 didn't open a run-application box. I discovered that I could create a blank file on the desktop, type a command in it, set its privileges to runnable, and execute it--I thought it might dodge conflicts in some way vs. trying to run stuff from 2 different ttys w/ CTRL+ALT+F2 etc.  

So after looking around in Nautilus via a desktop folder, trying "metacity --replace" per another thread ( [http://ubuntuforums.org/showthread.php?t=861448&highlight=panels](http://ubuntuforums.org/showthread.php?t=861448&highlight=panels) ) to no avail, and finding & running the gnome-panel-screenshot shortcut, I got into Synaptic by executing it through gksudo in that run-things file I created. I didn't find gnome-panel-screenshot in Synaptic, but I did find gonme-panel, and it wasn't installed.

I installed it, edited my run-things file to read "gnome-panel" (sans quotes), and got two error boxes: 
(1) 'The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet". Do you want to delete the applet from your configuration?'
(2) 'The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet". Do you want to delete the applet from your configuration?'

I figure I've borked my menus good, but I'm not sure which option I should choose in those error boxes.  Do I need to reinstall . . . hey, make that *install* . . . ubuntustudio-desktop?  I just looked in Synaptic, and it's not installed either.  Maybe removing evolution-data-server break my Ubuntu Studio suite and my panels en route?

+ + + Okay, hold the phone--it partially fixed itself, upon my opening an .avi file: Double-clicked the file in a Nautilus window and no sooner had Totem launched than both my top & bottom panels popped into view. My volume control & everything but the clock & power button are gone at top right, but even my custom icons are back to normal at left.  Weeeird . . . .  So I went ahead & installed ubuntustudio-desktop and that brought back my volume control etc. at top right.

---

### Post by Potatoj316 on 2008-07-18
If the panels are not installed try (in a terminal without quotes) "sudo aptitude install gnome-panel" then type your password.

---

