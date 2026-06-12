---
title: "Color Depth Problem"
date: 2009-01-07
forum: General Help
---

### Post by nikolaos on 2009-01-07
Well the problem goes like that...
I recently noticed that colors in firefox where not <<looking>> good, i suspected that it had something to do with the default color depth, so I checked the settings and everything seemed ok (ie 32bit), but then i typed 

```
xwininfo
```

and i got the following when i clicked on firefox

```
xwininfo: Window id: 0x30001ad "Google - Mozilla Firefox"

  Absolute upper-left X:  0
  Absolute upper-left Y:  49
  Relative upper-left X:  0
  Relative upper-left Y:  49
  Width: 1280
  Height: 725
  **Depth: 24**
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+49  -0+49  -0-26  +0-26
  -geometry 1280x725+0-26

```

when i clicked on the terminal window i got 

```
Absolute upper-left X:  4
  Absolute upper-left Y:  49
  Relative upper-left X:  4
  Relative upper-left Y:  49
  Width: 657
  Height: 435
  **Depth: 32**
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x3400003 (not installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +4+49  -619+49  -619-316  +4-316
  -geometry 80x24+4+49

```

and finally i tested on the file browser and got 

```
Absolute upper-left X:  88
  Absolute upper-left Y:  98
  Relative upper-left X:  88
  Relative upper-left Y:  98
  Width: 781
  Height: 550
  **Depth: 24**
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +88+98  -411+98  -411-152  +88-152
  -geometry 781x550+88+98

```

I googled but no one mentions any problem of the same kind!!!
Has anyone had a similar problem? How is it possible to have different color depth on different applications???


p.s Apologies for the long message!!!

---

### Post by nikolaos on 2009-01-18
can anyone post the output of 
```
xwininfo
```
pointing the mouse on firefox???

thanks in advance!!! :)

---

### Post by DeMus on 2009-01-18
> **nikolaos said:**
> can anyone post the output of 
```
xwininfo
```
pointing the mouse on firefox???

thanks in advance!!! :)

I did that three times, one time in the terminal, one time in Firefox and one on the bottom panel and all three said 24 bits.


I wish I could get 32 bits but I have no idea how to do that.
Maybe somebody can help.

---

### Post by DeMus on 2009-01-19
> **DeMus said:**
> I did that three times, one time in the terminal, one time in Firefox and one on the bottom panel and all three said 24 bits.


I wish I could get 32 bits but I have no idea how to do that.
Maybe somebody can help.

Nobody?

---

### Post by mcduck on 2009-01-19
The "24-bit colors" is exactly the same as "32-bit colors" in Windows. Calling them "32-bit" is misleading, as there really are only 24 bits of color data.

24 bits is as much as you can get on current displays, 8 bits for red, 8 bits for green and 8 bits for blue color channel. (8+8+8=24). The final 8 bits can be used for alpha channel (transparency), which is not a color channel at all and is only supported in certain situations and with certain file formats.

So, when it comes to color depth, 24-bit colors = 32-bit colors. Both display exactly the same amount of colors.

(Gnome-terminal uses full 32 bits, as it supports transparency)

edit: well, actually there are image formats that support more than 8 bits per color channel, but current display technology can't handle more so those formats are only used for special purposes, like professional print material etc.. All programs are still running at max. 24 bit color depth.

---

### Post by DeMus on 2009-01-19
> **mcduck said:**
> The "24-bit colors" is exactly the same as "32-bit colors" in Windows. Calling them "32-bit2 is misleading, as there really are only 24 bits of color data.

24 bits is as much as you can get, 8 bits for red, 8 bits for green and 8 bits for blue color channel. (8+8+8=24). The final 8 bits can be used for alpha channel (transparency), which is not a color channel at all and is only supported in certain situations and with certain file formats.

So, when it comes to color depth, 24-bit colors = 32-bit colors. Both display exactly the same amount of colors.

(Gnome-terminal uses full 32 bits, as it supports transparency)


Thank you for this explanation. Now I know I don't have to look any further.

---

### Post by nikolaos on 2009-01-19
Thanks for the explanation!!!

---

### Post by gillespieza on 2009-02-18
No, but knowing you mean 24 and not 32 still doesn't solve the problem. I have this same issue: my xorg.conf uses Defaultdepth 24, and xwininfo shows depth of 24, but it also shows Colormap: 0x20 (installed), and my system colours are still not right -- the lightest gray I can distinguish is #ccc -- any ideas?

---

### Post by yzarc on 2009-02-23
have you compiz activated? I have the same issue but only with the compiz activated. if I turn off the compiz and reboot, the color depth seems to be correct. but if I active the compiz the color depth seems to be automatically changed down. :( the images with gradients look like level curves (quiet ugly).

I think it's a bug of compiz+nvidia

---

