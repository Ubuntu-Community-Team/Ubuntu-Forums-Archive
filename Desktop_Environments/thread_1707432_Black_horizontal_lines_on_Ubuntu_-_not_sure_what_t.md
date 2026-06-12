---
title: "Black horizontal lines on Ubuntu - not sure what to do"
date: 2011-03-15
forum: Desktop Environments
---

### Post by MisterNeutral on 2011-03-15
I'm having an issue with horizontal black lines being displayed across certain applications. I'm running Ubuntu 10.10 and the latest nvidia driver. Here are my system specs:

cpu:                                                            
                       Intel(R) Pentium(R) Dual  CPU  E2220  @ 2.40GHz, 2400 MHz
                       Intel(R) Pentium(R) Dual  CPU  E2220  @ 2.40GHz, 2400 MHz
keyboard:
  /dev/input/event3    Microsoft Natural® Ergonomic Keyboard 4000
mouse:
  /dev/input/mice      Colorado USB Optical Mouse
graphics card:
                       nVidia GeForce 7300 LE
sound:
                       Dell Optiplex 755
storage:
                       Dell OptiPlex 755
                       Intel 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller

And here is a screenshot. 

[IMG]http://dl.dropbox.com/u/9908275/Screenshot-1.png[/IMG]

Any ideas?

---

### Post by randallecook on 2011-03-15
That's a weird one. Does it survive a system restart? Is it only with text, or all graphics? On all apps, or just some? I wonder if it has something to do with the font smoothing settings (System menu, Preferences, Appearance, Fonts).

An experiment you could try is when the lines are appearing in an app (like gedit, for instance), have the app print to a PDF and then view the resulting PDF on another machine. Did the lines get embedded in the PDF, or are they just a screen thing? This might help narrow down the problem.

---

### Post by MisterNeutral on 2011-03-15
Definitely there after restarts.

Lots of different apps, some it's only text, some it's menus in nautilus only.

It behaves differently based on the second. Sometimes when you open it lines certain apps, sometimes it lines others. The only one it reliably does it with is emacs.

---

### Post by MisterNeutral on 2011-03-17
I was able to solve this issue by turning off Compiz. A coworker believes that the nvidia driver is causing the issue.

You can turn off compiz by going to System -> Preferences -> Appearance, selecting the visual effects tab and setting it to "none."

---

