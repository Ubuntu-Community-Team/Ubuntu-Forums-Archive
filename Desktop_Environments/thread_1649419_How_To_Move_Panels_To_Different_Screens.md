---
title: "How To Move Panels To Different Screens"
date: 2010-12-20
forum: Desktop Environments
---

### Post by amtur_poet on 2010-12-20
I'm setting up a second monitor connected to my laptop via Twinview in the Nvidea settings manager for my system. It is working just fine, except for the fact that when I enable it, it puts the Desktop panels on the secondary screen, as opposed to the primary one. Is there any way to make new panels on the primary screen, or to move them over to the primary screen? I am running Ubuntu 10.10 64-bit on an HP Pavillion dv7 laptop.

---

### Post by amtur_poet on 2010-12-20
No ideas yet?

---

### Post by gogolink on 2010-12-21
Hi, I'm not using Twinview, but I had the same issue when I set up a second monitor on Ubuntu 10.10 on a MacIntel system: initially the external screen was treated as the primary monitor.  I *think* what solved it for me was this:

in **/[your home folder]/.config**, there should be a file called **monitors.xml**;

if you open the file with a text editor (might have to do it in sudo mode), and identify your laptop monitor by its resolution (assuming it's different from that of your external monitor), you should see a line that might read "<primary>no</primary>"

So you change the "no" to "yes", save (as sudo), and next time as you log in (not before: won't do anything to splash screen), your laptop monitor should be set as primary.

Here's a segment of my monitors.xml; my laptop screen resolution is 1200x800:

[PHP]<output name="LVDS1">
          <vendor>LPL</vendor>
          <product>0xdc00</product>
          <serial>0x00000000</serial>
          <width>1280</width>
          <height>800</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>yes</primary>[/PHP]

---

### Post by gogolink on 2010-12-21
Oh, and to move panels from one screen to another, you should simply have to do the following: 

Right-click the panel you wish to move and select “Properties”;
uncheck the “Expand” option under the “General” tab;
grab one of the edges of the panel by clicking on the left or right end (top or bottom end for vertical panels;
drag the bar to the desired screen and position;
check the “Expand” option in the “Panel Properties” window and click “Close”.

---

### Post by wojox on 2010-12-21
When you open a terminal and run

```
gksudo nvidia-settings
```

you should be able to set which screen is primary.

---

