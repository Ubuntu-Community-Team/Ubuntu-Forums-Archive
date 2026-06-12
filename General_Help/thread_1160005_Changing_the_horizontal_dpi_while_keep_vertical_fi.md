---
title: "Changing the horizontal dpi while keep vertical fixed"
date: 2009-05-15
forum: General Help
---

### Post by emnaki on 2009-05-15
I have a 800x480 touchscreen and I am using a crap VIA (can't use xrandr) graphics card (can't change here). I have to rotate my screen and luckily I can do this in xorg.conf by setting
```
Option "Rotate" "CCW"
```
in the device section for my VIA.
The problem is that I can't reduce vertical dimension below 1:1. I managed to get somewhere by setting:
```
Viewport 0 0
Virtual 800 800
```
My desktop then fits vertically but stretches beyond the horizontal. This ia not that much of a problem I just have to scroll. The biggest problem is that the everything is vertically stretched. So I am thinking if reducing the horizontal dpi while keeping vertical fixed will solve the problem. But how do you do this?

Also other approaches to solving this problem would be greatly appretiated!

---

