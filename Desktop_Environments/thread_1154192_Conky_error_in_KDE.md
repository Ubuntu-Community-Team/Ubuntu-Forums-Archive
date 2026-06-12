---
title: "Conky error in KDE"
date: 2009-05-09
forum: Desktop Environments
---

### Post by Delirium_Trigger on 2009-05-09
I'm using Ubuntu Jaunty and installed KDE earlier today.
While tweaking things to my liking, terminal gave me this error when I tried starting Conky.

```
justin@justin-laptop:~/Documents$ conky
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: forked to background, pid is 28761
justin@justin-laptop:~/Documents$ 
Conky: desktop window (140025d) is subwindow of root window (9a)
Conky: window type - override
Conky: drawing to created window (0x2400001)
Conky: drawing to double buffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  2 (X_ChangeWindowAttributes)
  Serial number of failed request:  208
  Current serial number in output stream:  209
```

Edit: Attached my conky file

---

### Post by VCoolio on 2009-05-09
Probably the problem is the setting "own_window_transparent yes". Change that to no, specify a window color with e.g. "own_window_colour red" and see what happens. If conky shows up, your composite manager doesn't like what conky does with transparency. I´m no KDE-guy, so this is all I can give. I had the same with ecomorph on enlightenment (unsolved so far).

---

### Post by Delirium_Trigger on 2009-05-10
I tried and got nothing.
When I hit alt+f2 and type in conky the entire desktop turns white (panel is still visible). 

Conky works so great in Gnome and I'm really intrigued by KDE.
I don't want this to be the one thing that turns me off KDE entirely.

---

### Post by vikrant82 on 2009-05-10
The problem seems to be with :
"own_window_type override"

You should set it to normal. There has been age old issues with getting transparent conky on KDE. 

One easy workaround is to install a cool command line image viewer - "feh"

```
sudo apt-get install feh
```

Next add following command to your conky at the end..
```

${texeci 10 feh --bg-scale /usr/share/wallpapers/Air/contents/images/1280x800.jpg}
```

The number 10 should be greater than your conky refresh time.. Play around with other options of feh.

---

### Post by Delirium_Trigger on 2009-05-10
Your method seemed to help.. some..
I attached a screenshot.

The window has a border, which I would like to get rid of; any suggestions?
Also, my Conky is full of random boxes.
What's with that?!

---

