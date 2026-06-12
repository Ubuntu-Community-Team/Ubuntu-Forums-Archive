---
title: "Faking Multiple Displays"
date: 2010-02-05
forum: Desktop Environments
---

### Post by Tindytim on 2010-02-05
I've always wondered if there was a way to fake multiple displays, and define how the single display was divided. For example, I have multiple devices with >16:9 aspect ratios (1024x600 is becoming more common for some reason). Is there someway I could fake two 512x600 displays? or maybe two 32x600 sections and one 16:10 940x600 section?

Thoughts or suggestions?

---

### Post by weblordpepe on 2010-02-05
Yeah mate. You could run two X windows inside one X server. [http://ubuntuforums.org/showthread.php?t=620003](http://ubuntuforums.org/showthread.php?t=620003)

---

### Post by x33a on 2010-02-05
I don't think that i understand you correctly, but you may be wanting tiling windows managers.

[http://en.wikipedia.org/wiki/Tiling_window_manager](http://en.wikipedia.org/wiki/Tiling_window_manager)

some good ones: dwm, xmonad, ratpoison, awesome, etc.

---

### Post by weblordpepe on 2010-02-05
I think he's wanting to fake multiple displays, so to me that means fake X servers. I suggest trying this out. It'll give you a fake X display inside a window on your desktop.

Here dude try this out. 

First open a terminal window (look for it in the Applications window)

Install Xephyr. 
```
sudp apt-get install xserver-xephyr
```

Then run the following as a normal regular user:
```
Xephyr -ac -screen 640x480 :2 2> /dev/null &
```

What that does will start a blank X window. The above command launched this Xephyr X server, called it display :2, diverted the error outputs to nowhere (/dev/null) and returned your command prompt back to you (the & at the end).

Now when you type programs on the command line with this, programs will want to know which X server to use. Either your regular one or this new one you made. The new one is called 2.0 and the original is called 0.0.

To do this, type:
```
DISPLAY=2.0
```
All programs you type in that terminal window will run inside your windowed X session.  But there's of course no window management, which sucks. You'll want to load something into that windowed X display to manage windows etc. 

type
```
gnome-wm &
``` again with the & to return your command prompt to you.

Nothing will appear to happen. Type:
```
xcalc
```
That will load the basical calculator, and it will have a window title etc so you can move it around. 


That DISPLAY=:2.0 bit is only valid for whatever terminal youre running in. It goes back to normal when you open a new one.

Feel free to close the terminal window now. Any time you want to run a program in that windowed X server, what you type to run the program will need to be prefixed with **DISPLAY=:2.0 &&**

For example.
```
DISPLAY=:2.0 && vlc
```

That'll launch VLC into the windowed X display

---

### Post by Tindytim on 2010-02-05
Tiling isn't what I had in mind. I'm thinking I might be able to add multiple screens in the xorg.conf. I'm trying it with VMware atm, and I'll post my results either later today, or early next week.

Since I have a multi-display setup on my main machine, I simply want a divided screen , so I could essentially maximize applications in one section, while keeping them useful. I'm currently viewing this site on a 1920x1200 monitor, and it is slightly annoying how much text there is in a single line. And this display is 16:10, there are many more devices with wider aspect resolutions.

---

### Post by x33a on 2010-02-05
If you want to emulate multiple physical monitors, then workspaces should work fine for you.

if you want to actually use more than one physical monitors, then take a look here:

[http://en.wikipedia.org/wiki/Xinerama](http://en.wikipedia.org/wiki/Xinerama)

[http://en.wikipedia.org/wiki/XRandR](http://en.wikipedia.org/wiki/XRandR)

---

### Post by falconindy on 2010-02-05
> **Tindytim said:**
> Tiling isn't what I had in mind. I'm thinking I might be able to add multiple screens in the xorg.conf. I'm trying it with VMware atm, and I'll post my results either later today, or early next week.

Since I have a multi-display setup on my main machine, I simply want a divided screen , so I could essentially maximize applications in one section, while keeping them useful. I'm currently viewing this site on a 1920x1200 monitor, and it is slightly annoying how much text there is in a single line. And this display is 16:10, there are many more devices with wider aspect resolutions.
You've just described exactly how tiling works. I'm using a tiling WM, DWM, which looks like this:

[[img]http://dwm.suckless.org/screenshots/dwm-20070930s.png[/img]](http://dwm.suckless.org/screenshots/dwm-20070930.png)

As an added bonus, the only time I use a mouse is for web browsing.

You'll find that tiling WMs have somewhat of a cult following. There's no way you'll ever get me back to a DE like Gnome or KDE just because they're so mouse-centric. Being forced to use two input devices when one will suffice is a huge bane on productivity. I'll get off my soapbox now.

DWM isn't alone... there's plenty of others:

* XMonad
* RatPoison
* StumpWM
* ScrotWM
* Musca
* TWM
* wmii
* awesome

the list goes on...

---

### Post by weblordpepe on 2010-02-05
> **Tindytim said:**
> Tiling isn't what I had in mind. I'm thinking I might be able to add multiple screens in the xorg.conf. I'm trying it with VMware atm, and I'll post my results either later today, or early next week.

Since I have a multi-display setup on my main machine, I simply want a divided screen , so I could essentially maximize applications in one section, while keeping them useful. I'm currently viewing this site on a 1920x1200 monitor, and it is slightly annoying how much text there is in a single line. And this display is 16:10, there are many more devices with wider aspect resolutions.

You are after nested X servers. Did you read my post? It describes exactly what you're after. The ability to divide your screen into virtual displays. These are treated like real displays, as real as your regular one, as if you had multiple monitors.

---

### Post by Brandon_oma#692 on 2010-02-05
> **x33a said:**
> If you want to emulate multiple physical monitors, then workspaces should work fine for you.
 
if you want to actually use more than one physical monitors, then take a look here:
 
[http://en.wikipedia.org/wiki/Xinerama](http://en.wikipedia.org/wiki/Xinerama)
 
[http://en.wikipedia.org/wiki/XRandR](http://en.wikipedia.org/wiki/XRandR)
 
 
Can you direct me to more information on this? How to physicall connect the screens. and the installation of the Xinerama or similar software. (new user trying to learn here)

---

### Post by x33a on 2010-02-05
> **Brandon_oma#692 said:**
> Can you direct me to more information on this? How to physicall connect the screens. and the installation of the Xinerama or similar software. (new user trying to learn here)

As for physically connecting multiple monitors: 

[http://en.wikipedia.org/wiki/Multi-monitor](http://en.wikipedia.org/wiki/Multi-monitor)

for configuring ubuntu to use more than one monitor:

[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

---

### Post by weblordpepe on 2010-02-06
> **Brandon_oma#692 said:**
> Can you direct me to more information on this? How to physicall connect the screens. and the installation of the Xinerama or similar software. (new user trying to learn here)Hi dude.
Basically X is the display engine that UNIX and linux use for handling displays. The nifty thing is that its network-aware and is totally virtualized.

All programs (all of them) which draw any kind of graphics are talking to the one, default X server running on your computer. Each program is a client which talks to the X server, which is glued to your monitor.

Now you can have an X server anywhere on anything you like. You simply set a variable (ill explain this later) which tells all programs which X server to use,

If you bring up a terminal and type **echo $DISPLAY** it should show **:0.0**
Thats the variable which is set to display 0 by default. By changing that to **:2.0** all programs will start using X server 2. Which could be anything you have running. It could be in japan for all we care :)

In the above posts I was showing that guy how to set up the Xephyr program (an X server program) to set up display 1, display 2, etc etc. The wacky thing about Xephyr is that its a virtual X server which runs inside a window of a normal X server. So its like a magical virtual X server if ya get me.

I hope this makes sense to ya.

---

### Post by Brandon_oma#692 on 2010-02-07
> **weblordpepe said:**
> Hi dude.
Basically X is the display engine that UNIX and linux use for handling displays. The nifty thing is that its network-aware and is totally virtualized.
 
All programs (all of them) which draw any kind of graphics are talking to the one, default X server running on your computer. Each program is a client which talks to the X server, which is glued to your monitor.
 
thanks i got the first part and second part kinda but the rest went way over my head.
 
> **weblordpepe said:**
> 
Now you can have an X server anywhere on anything you like. You simply set a variable (ill explain this later) which tells all programs which X server to use,
 
If you bring up a terminal and type **echo $DISPLAY** it should show **:0.0**
Thats the variable which is set to display 0 by default. By changing that to **:2.0** all programs will start using X server 2. Which could be anything you have running. It could be in japan for all we care :)
 
In the above posts I was showing that guy how to set up the Xephyr program (an X server program) to set up display 1, display 2, etc etc. The wacky thing about Xephyr is that its a virtual X server which runs inside a window of a normal X server. So its like a magical virtual X server if ya get me.
 
I hope this makes sense to ya.

---

