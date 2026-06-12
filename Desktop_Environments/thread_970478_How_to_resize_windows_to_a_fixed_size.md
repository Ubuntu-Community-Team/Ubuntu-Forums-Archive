---
title: "How to resize windows to a fixed size"
date: 2008-11-04
forum: Desktop Environments
---

### Post by Rajin on 2008-11-04
Hi, I'd want to know if there is a method to resize GNOME's windows to a defined size. For example, I'd like to set a window to 500x350px, but I haven't found any resizing method but the manual tool. Do you know how I can do this?

---

### Post by jastonas on 2008-11-04
Dont know the answer, but do you think its also possible to make different default sizes depending on the application? I mean, different for folders, for firefox windows, for terminals etc..

---

### Post by Rajin on 2008-11-04
No, this is not what i mean. What i need is a tool or an option to choose the size of a window in GNOME, as the normal resize tool, but that gives me the possibility of choose the exact size of the window.

---

### Post by julio prada on 2011-05-23
In Ubuntu 11.04 I found a "Config Compiz Settings manager" icon that indicates the window size, you can not write the numbers but you can resize each side with the mouse and get the desired result.
It is called " Resize info"

---

### Post by stinkeye on 2011-05-24
You can use wmctrl to resize and position a window with
```
wmctrl -r :ACTIVE: -e g,x,y,w,h
```
g...gravity (just leave as the default 0)
x...horizontal position of the top left corner of the window
y...vertical position of the top left corner of the window
w...width
h...height

eg to suit my screen res I use this to resize and centre a focused window.
```
wmctrl -r :ACTIVE: -e 0,400,200,875,550
```
You can bind your command to a key in keyboard shortcuts or edge/button in compiz.

Search in the software centre for wmctrl or install through the terminal.
```
sudo apt-get install wmctrl
```

---

### Post by Copper Bezel on 2011-05-24
wmctrl would be the best option for the OP. Commands can be bound to Compiz command keybindings.

> Dont know the answer, but do you think its also possible to make different default sizes depending on the application? I mean, different for folders, for firefox windows, for terminals etc..

Compiz Window Rules has a tab called Size Rules that can do this, but there's no way to resize a window at all if it has a size fixed.

Gnome Terminal's Profile Preferences can set the default size of a terminal in characters and rows, but if the number of characters per row is below 80, you'll break the manual pages.

---

