---
title: "Emacs Frame/Window size"
date: 2007-12-03
forum: Desktop Environments
---

### Post by yasdnil on 2007-12-03
Hi,

Can anyone help me set the default frame/window size on Emacs. I want to set the height to the full height of the screen (minus the tip and bottom menu bars of course), and I want the width to be exactly half of the width of my monitor. 

I am a newbie Ubuntu user, having previously used emacs on Mac OS X. I gather that in Ubuntu, I need to put something in my .Xresources file. Not sure what. 

Any help much appreciated.

yasdnil

---

### Post by Chas_E_Erath on 2007-12-03
I'm not so bright on these things - maybe even a little kludgy - but what I tend to do with this sort of thing is: 
- open a window, resize and locate to the your preferences
- type xwininfo in an xterm (or some such) and click on the emacs window.

the last line of the output gives you the window geometry.  ie:

```
chas@stinker ~ # xwininfo 

xwininfo: Please select the window about which you
          would like information by clicking the
          mouse in that window.

xwininfo: Window id: 0x10001dd (has no name)

  Absolute upper-left X:  463
  Absolute upper-left Y:  56
  Relative upper-left X:  4
  Relative upper-left Y:  23
  Width: 238
  Height: 563
  Depth: 24
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
  Corners:  +463+56  -979+56  -979-431  +463-431
  -geometry 39x43+459+33

  

```


After that,  create an alias in your .bashrc (or what have you).  If launching from an icon click, modify the icon command to read something like:

```
emacs  -geometry 39x43+459+33
```

Hope that helps, but you're right, there's likely a cleaner way using your .Xresources file.

---

