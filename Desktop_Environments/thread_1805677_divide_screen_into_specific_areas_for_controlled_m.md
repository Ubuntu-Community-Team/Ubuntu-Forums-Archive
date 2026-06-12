---
title: "divide screen into specific areas for controlled maximising of windows"
date: 2011-07-16
forum: Desktop Environments
---

### Post by deltaluca on 2011-07-16
(ubuntu 10.4, gnome)

In windows i used a program called MaxTo to do this.

I'm not asking on a way to literally split the screen into sub-screens. Rather I only want it to manipulate the way that maximising windows works in a general way.

The way it works in windows with maxTo is that you define splits for each screen and then by default when you maximise any window, it only maximises into that region of the screen in which it's contained (or with keyboard modifier, maximises to the entire screen).

This is very handy with larger screens to help layout windows easily without having to place/resize by hand to have them fit side by side without overlaps.

---

### Post by rickytikki on 2011-07-16
are you talking about the windows snapping effect

---

### Post by rickytikki on 2011-07-16
if that what it is look into compiz effects and lok fore windows management and select windows snapping

---

### Post by deltaluca on 2011-07-16
the graphic at the top of the maxto homepage [http://www.maxto.net/](http://www.maxto.net/) pretty much describes it in a nutshell (2. and 3.) the screen is divded into regions, and when a window is maximised it fills only that region rather than the whole screen.

with more googling i've found what it's more precisely called is a window tiling manager. I gave xmonad a quick try but it's a bit more than i want/need. All i want is to control the maximising, nothing more advanced/complicated than that.

---

### Post by deltaluca on 2011-07-16
Looking at some more managers, they all seem to offer a bit more than i want. Mainly i don't want to enforce the tiling in any way. only to have it so when they screen is maximised it fills the tile; otherwise i want everything to be free as usual. Aswell as having finite number of fixed tiles; rather than dynamically changing with number of windows etc.

---

### Post by deltaluca on 2011-07-16
Okay, I've found a solution to this by writing a script to be executed which grabs the information abuot the active window (through xwininfo) and uses wmctrl to then reposition/resize it to the defined region based on the windows current position.

So I guess to finalise this solution, i need a way to bind this action to the maximise button on the gnome windows. Any ideas?

---

### Post by rickytikki on 2011-07-16
Really??? stop bieng lazy and just resize the windows. plus its basically windows snap

---

### Post by linuxNooby?? on 2011-07-16
> **rickytikki said:**
> Really??? stop bieng lazy and just resize the windows. plus its basically windows snap
i have the same problem kind of but my task bar thing disappeared so now i have no left task bar. Oh, by the way I'm running ubuntu 11.4. But after that all I had on the desktop was the application, places and system bar at the top like in 10.4
Sry never mind wrong post.

---

### Post by Krytarik on 2011-07-16
> **rickytikki said:**
> Really??? stop bieng lazy and just resize the windows. plus its basically windows snap
Really!? This has nothing do with "Snapping Windows", plus, I understand the reasoning behind this. And the way the OP has chosen is imo the only possible way. But unfortunately, I don't think it's possible to bind those script to the maximize button.

---

### Post by stinkeye on 2011-07-18
Something else that you may not be aware of is that if you right click on the maximize button the window will maximize horizontally
and a middle click will maximize vertically.

---

