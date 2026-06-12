---
title: "Anyone know how to scroll entire desktop?"
date: 2009-02-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Rallg on 2009-02-15
I use U 8.10 on my mini 9, without compiz and with only one desktop.

Sometimes, and application generates a dialog box that is too tall for the screen. This is a real problem with the small vertical pixel size for this screen. The dialog buttons (OK, Cancel, whatever) are invisible, and cannot be brought into view by moving the dialog box or by scrolling anything obvious.

Is is possible to move (translate X or Y) the entire desktop? Think of the way that some drawing applications have a work area that is much larger than the canvas size.

I have tried obvious key combinations to no avail (not that I know many key combinations).

The desktop is 1024x600. I imagine a workspace 1024x800, with the bottom 200 accessible if the desktop is moved.

---

### Post by ugm6hr on 2009-02-15
Try pressing the Alt key and holding the left-click mouse (Touchpad) button over any part of an open window.  Then move the mouse around.

---

### Post by Rallg on 2009-02-15
Thanks. That seems very useful. I would never have thought of it. The visual effect is different than I had imagined, but it works.

---

### Post by Kareeser on 2009-02-16
Problem's well documented, with the rise of netbooks these days.

Expect 9.10 to come with better autodetection and window resizing if you're using a netbook :)

---

### Post by Rallg on 2009-02-17
I can hardly wait! Would have liked it in 9.04, though.

Part of the problem is not screen size detection. It is that some of the dialog boxes are very wasteful of space. If they were more compact, they would fit.

---

### Post by silvari on 2009-03-07
I'm having a similiar issue. I'm running Crunchbang Linux (based on Ubuntu 8.10) on an HP Mini 1030NR. The screen res is 1024x600. I'm not able to access the buttons on the dialog box which extends passed the bottom of the screen. I've tried the alt-left-click trick above, and instead of moving the whole dialog-box upwards, it just moves the top border (therefore making the box taller) and the buttons I'm looking for, stay hidden beyond the bottom of the screen.

The specific dialog box I'm dealing with, is from Gnumeric (spreadsheet app) ; [Data][Get External Data][Import Text File]. After selecting the file I want, another box titled "Text Import Configuration" appears. Towards the bottom, the first x records of the text file are listed in a scrollmenu. When I try the alt-left-click trick, it just causes this list to grow.

Any help would be greatly appreciated. Thanks!

---

### Post by Rallg on 2009-03-07
Silvari, try this: use Alt + leftClick to move the top bar of the dialog box down, which shrinks the box. Then, move the whole box up.

---

### Post by ugm6hr on 2009-03-08
When you Alt-Left click, make sure you are clicking *inside* the window, not on the Title bar.

This suggests openbox (the WM in Crunchbang) uses the same shortcut:
[http://www.gbar.dtu.dk/index.php/Openbox](http://www.gbar.dtu.dk/index.php/Openbox)

Otherwise, try Windows key + Up arrow:
[http://urukrama.wordpress.com/2008/07/22/my-openbox-keybindings/](http://urukrama.wordpress.com/2008/07/22/my-openbox-keybindings/)

It looks like you can edit all the various keybindings, so it is possible Crunchbang uses non-default settings.

If you don't find a solution, ask on a Crunchbang or Openbox forum.

---

### Post by sirebral on 2009-03-08
I had a slightly different idea after reading this, but it takes a little more then the pre-installed software.

If you run Compiz as your window manager (I use Emerald and Fusion Icon for this), then you will have a Desktop Wall.  Then I setup Workspace Switcher to have two rows and now columns.  

What I get is two desktops that are top to bottom.  With Desktop Wall active (it is a Compiz Feature) windows will spill over to the next desktop.

One thing I like about Fusion Icon is that I an turn Compiz off really quickly, that is why I suggest Fusion Icon.

---

### Post by samadams on 2009-05-28
I have the same problem with various apps, VLC to be specific at the moment, and I am not using compiz.  I'm on 9.04 but have had this problem since 6.04.  And this occurs with a screen size of 800 and even larger depending on the dialog box size.  It seems that the apps in question are setting a fixed height to the box rather than let Ubuntu dynamically manage it according to screen resolution.  (I suspect this because the ALT+F8 Resize option only works horizontally, and not vertically, and the fact that some other apps do have their boxes scroll.)

I can't get the box to shrink at all, but the ALT+Click does let me move it around to see the whole thing if not all at once.

If this is an OS bug, it should be at the top of the heap to fix.  I'm here to stay, but I can't imagine the average Joe switching from MS having to put up with this.  They'll quickly switch back.

---

