---
title: "Widescreen weirdness after Gutsy Upgrade"
date: 2007-10-20
forum: Desktop Environments
---

### Post by orbital13 on 2007-10-20
After I upgraded from Feisty to Gutsy I now have a weird display issue. I have a Dell 2005FPW 1680x1050 monitor. Running xpdyinfo shows that everything is being recognized correctly:

```


screen #0:
  dimensions:    1680x1050 pixels (431x272 millimeters)
  resolution:    99x98 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x52
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    1680x1050
  current input event mask:    0xfa0073
    KeyPressMask             KeyReleaseMask           EnterWindowMask          
    LeaveWindowMask          PointerMotionMask        StructureNotifyMask      
    SubstructureNotifyMask   SubstructureRedirectMask FocusChangeMask          
    PropertyChangeMask       ColormapChangeMask       
  number of visuals:    4

```

Using Envy to re-install nvidia drivers did nothing. I'm attaching a screenshot illustrating the issue. Basically I can only see the stuff in the upper left hand corner of the screenshot. Everything in black is off my screen. 


[IMG]http://www.lynucs.org/index.php?screen_type=2&screen_id=49172767471a3481a3bca&m=screen[/IMG]

I'd appreciate any pointers, I couldn't find anything exactly like this on Googl, the forums or the wiki. 

Thanks.

---

### Post by orbital13 on 2007-10-20
I've kinda solved this by bumping down my refresh rate to 50HZ. The lower the refresh rate, the more screen space I can see.

---

### Post by burningbed on 2007-10-21
I have had a perhaps somewhat similar problems (see [http://ubuntuforums.org/showthread.php?t=583642]("http://ubuntuforums.org/showthread.php?t=583642")) and they were all solved by uninstalling xserver-xgl.
I'd try running running apt-get remove xserver-xgl and see if it helps.

---

