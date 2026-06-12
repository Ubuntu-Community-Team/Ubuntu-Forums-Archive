---
title: "Compiz Fusion and no cube..."
date: 2007-06-22
forum: Desktop Effects &amp; Customization
---

### Post by fycloops on 2007-06-22
So I am trying fusion. In Beryl I love the cube but it isn't working in Fusion. I have enabled the options of "Desktop Cube" and "Rotate Cube" in "CompizConfig Settings Manager" but no joy.

Running Feisty. 
Nvidia card.

Beryl still works fine when I switch back to it.

Any ideas? Am I missing something basic?

Fyc

---

### Post by Vorian on 2007-06-22
Might want to check how many desktops you have set up.  You can find that in the general section of the Settings Manager.

Also make sure you check the behaviors of the cube and rotate cube sections.

---

### Post by fycloops on 2007-06-22
Number of Desktops = 1

What should I be looking for in behaviours of the cube?

It looks like it is behaving as the Desktop Wall even though this is disabled and cube is enabled...

Fyc

---

### Post by Vorian on 2007-06-22
you need 4 horizontal desktops for a cube.

---

### Post by Ultra Magnus on 2007-06-22
To get the cube you want to change the horizontal virtual size (under general settings) - although when I downloaded it, it was already set as that as default.

---

### Post by fycloops on 2007-06-22
Yeah. 

Horizontal Virtual size is 4.

Vertical Virtual Size is 1

Number of Desktops is 1

Fyc

---

### Post by smartboyathome on 2007-06-22
You need 4 (four) desktops to use the cube. It won't work otherwise. And it doesn't embed itself in your wallpaper, it is used to switch between desktops.

---

### Post by Vorian on 2007-06-22
If you're not familiar with Compiz this is how you get the Cube to rotate:
ctrl+alt+left/right arrow or ctrl+alt+left mouse button.

---

### Post by fycloops on 2007-06-22
OK I got it sorted. When I originally used the command "compiz --replace" something went wrong. Maybe something to do with having beryl going when I did it.

So I have done it again after quitting beryl and all the settings are working now.

Sorry for the muck around and thanks for the input!

Fyc

---

### Post by waggygee on 2007-07-11
> **fycloops said:**
> So I am trying fusion. In Beryl I love the cube but it isn't working in Fusion. I have enabled the options of "Desktop Cube" and "Rotate Cube" in "CompizConfig Settings Manager" but no joy.

Running Feisty. 
Nvidia card.

Beryl still works fine when I switch back to it.

Any ideas? Am I missing something basic?

Fyc

I have the same problem plus I dont have borders on my wimdows, when I run the command "compiz --replace" I get this

XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 133 requests (132 known processed) with 0 events remaining.
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

May I add that my terminal appears as a white square with no writting.:(
and when I run this command 'compiz --replace -c emerald &' I get the cube and all the compizfusion effects/plugins running but still no windows borders

---

### Post by jase21 on 2007-11-18
Thanks 
Horizontal Virtual size is 4.

Vertical Virtual Size is 1

Number of Desktops is 1

is right

---

