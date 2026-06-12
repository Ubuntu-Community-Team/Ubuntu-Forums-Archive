---
title: "Can not set external monitor  to left of internal monitor on ubuntu 17.04"
date: 2017-07-10
forum: Desktop Environments
---

### Post by caneraydinbey on 2017-07-10
When i connect external, and when i go to display settings, the external is in right of internal.


I change in this settings by dragging, then apply to set to the left of the internal.


But it makes black external and i have to plug out and plugin again to be able to use external and it is again on the right of internal.


this is xml of monitors


sudo gedit ~/.config/monitors.xml


```
    <monitors version="1">
      <configuration>
          <clone>no</clone>
          <output name="eDP-1-1">
              <vendor>AUO</vendor>
              <product>0x44ed</product>
              <serial>0x00000000</serial>
              <width>1920</width>
              <height>1080</height>
              <rate>60</rate>
              <x>0</x>
              <y>0</y>
              <rotation>normal</rotation>
              <reflect_x>no</reflect_x>
              <reflect_y>no</reflect_y>
              <primary>yes</primary>
          </output>
          <output name="HDMI-1-1">
              <vendor>PHL</vendor>
              <product>0xc0c5</product>
              <serial>0x00001e7f</serial>
              <width>1920</width>
              <height>1080</height>
              <rate>60</rate>
              <x>1920</x>
              <y>0</y>
              <rotation>normal</rotation>
              <reflect_x>no</reflect_x>
              <reflect_y>no</reflect_y>
              <primary>no</primary>
          </output>
      </configuration>
      <configuration>
          <clone>no</clone>
          <output name="eDP-1-1">
              <vendor>AUO</vendor>
              <product>0x44ed</product>
              <serial>0x00000000</serial>
              <width>1920</width>
              <height>1080</height>
              <rate>60</rate>
              <x>0</x>
              <y>0</y>
              <rotation>normal</rotation>
              <reflect_x>no</reflect_x>
              <reflect_y>no</reflect_y>
              <primary>yes</primary>
          </output>
          <output name="HDMI-1-1">
              <vendor>PHL</vendor>
              <product>0xc0c5</product>
              <serial>0x00001e0c</serial>
              <width>1920</width>
              <height>1080</height>
              <rate>0</rate>
              <x>1920</x>
              <y>0</y>
              <rotation>normal</rotation>
              <reflect_x>no</reflect_x>
              <reflect_y>no</reflect_y>
              <primary>no</primary>
          </output>
      </configuration>
    </monitors>
```

---

### Post by aromo2 on 2017-07-10
I never use command line to configure the second monitor. Install ARandr (from software centre) and do it via menus. Hope it helps.

---

### Post by Bucky Ball on 2017-07-10
> **aromo2 said:**
> Install ARandr (from software centre) and do it via menus.

+1. Might make your life easier.

Might be silly question, but are you trying this plugging in the external monitor while your computer is on? If so, switch all off, plug in the monitor and switch it on, *then* switch on the computer and see if it picks it up correctly 'automagically'. Failing that, arandr. It is in the repostories (Software) or via command line:

```
sudo apt install arandr
```

And yes, at this point, delving into code not necessary. ;)

---

### Post by caneraydinbey on 2017-07-10
YEs after starting, i am plugging. I will try

---

### Post by deadflowr on 2017-07-10
> 
sudo gedit ~/.config/monitors.xml

Don't run this command, you only need gedit filename.
```
gedit ~/.config/monitors.xml
```
Running sudo to open graphical apps can cause problems.
And there is never a need to run it with anything that you already have the ability to deal with yourself.
(You own the file so no need to elevate yourself to root, if you know what I mean)

---

### Post by caneraydinbey on 2017-07-11
I tried  arandr. Sometimes when i move to left of internal, i cant set. So i have to plug out and in again to fix.

---

### Post by Bucky Ball on 2017-07-11
Yea, the plugging out and in while the computer is on is not great. Like I said, switch everything off, plug the monitor in and switch it on (and set to correct source input). Once that's stable (no signal), switch on the computer. Have you actually tried that yet??? You said you would and have since not mentioned it or your result trying it.

Yanking the cable in and out while the machine on is not going to get you far and won't give realistic results. Just do as above and work from there. Physically yanking cable is not going to fix anything. This is 99% likely to be a system setting (unless you have a dead or faulty cable, in which case, replace).

I'm still not convinced that if you try what I'm trying to tell you, then it may just work 'automagically'. Always has for me. Shoving in the monitor while your booted up, logged in at a desktop is, yea, going to present unpredictable results and may be confuse things as far as the OS goes.

Leave you with it. Good luck. ;)

---

