---
title: "How make mouse pointer to turn-around desktop after exiting from one side?"
date: 2011-01-23
forum: Desktop Environments
---

### Post by WthIteh on 2011-01-23
There are pretty good graphical features on gnome. But I could not find a nice feature, allowing mouse pointer to turn-around the desktop area.
I want the mouse pointer goes to left side of screen when it reaches right side of desktop and vice versa. Or goes to bottom of the desktop area when it reaches top of screen. It makes using mouse and moving around the desktop area using a touchpad easier.
Is it possible? If yes, how?

---

### Post by Krytarik on 2011-01-24
It's apparently always worth to be here! One gets the inspiration to explore functions oneself hasn't thought about before. I've just yet learned how to use xdotool, with it you can achieve your desired function.

If you have 10.10 running, you can install it right from the archive:
```
sudo apt-get install xdotool
```If you have 10.04, like me, you have to activate a backports ppa to get a more recent version, deactivate it after installing xdotool!:
[https://launchpad.net/~bdrung/+archive/backports]("https://launchpad.net/%7Ebdrung/+archive/backports")

Then you can use it's option "mousemove_relative".

The following command for example moves the mouse cursor from the upper edge to the same horizontal position at the bottom edge, my screen resolution is 1152x864:
```
xdotool mousemove_relative polar 180 864
```[http://www.semicomplete.com/projects/xdotool/xdotool#mouse_commands](http://www.semicomplete.com/projects/xdotool/xdotool#mouse_commands)

To activate those commands when the mouse is at the respective edges, use Compiz' settings:
- go to "System -> Preferences -> CompizConfig Settings Manager -> Commands"
- enter the commands in the first tab, "Commands"
- go to the "Edge Bindings" tab
- assign the proper edge to each command

Good luck, ask if something is unclear!

---

### Post by WthIteh on 2011-01-24
Wow :D Really Great!!!!! :KS

Just one note for others who may want to enable this fantastic feature :)
My screen height is 768 and if I use 768 for movement distance, then mouse will fall in an infinite movement loop. When mouse goes to top edge, it will be moved to down edge and then down edge command will be triggered and move mouse to top edge again and again.
So it is required to use a smaller movement distance like 760 instead of 768 so mouse does not reach next edge.

Very thanks for your advice :)

---

### Post by BHEJU on 2011-01-24
Very interesting feature. I like it.

---

### Post by Krytarik on 2011-01-24
> **WthIteh said:**
> Wow :D Really Great!!!!! :KS

Just one note for others who may want to enable this fantastic feature :)
My screen height is 768 and if I use 768 for movement distance, then mouse will fall in an infinite movement loop. When mouse goes to top edge, it will be moved to down edge and then down edge command will be triggered and move mouse to top edge again and again.
So it is required to use a smaller movement distance like 760 instead of 768 so mouse does not reach next edge.

Very thanks for your advice :)
Hahaha, I didn't take that into account. Great that it works!!:D I haven't actually tested it completely, as you witnessed.

---

