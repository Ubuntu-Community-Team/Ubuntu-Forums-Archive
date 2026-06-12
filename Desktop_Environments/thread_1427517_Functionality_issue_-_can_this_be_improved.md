---
title: "Functionality issue - can this be improved?"
date: 2010-03-11
forum: Desktop Environments
---

### Post by keforex on 2010-03-11
I don't know if it's just me, but there is one annoyance that if you guys have a way to solve it would be greatly appreciated.

I resize windows all the time (I have two 30" monitors) and every time I try to position the mouse cursor at any of the edges or corners of any window it is ALWAYS a pain because the cursor only stays in "resize" mode for 1 fraction of a millimeter, I believe just one pixel... So unless I have a super steady hand it takes me a while to "grab" the window to resize it.

Since I have two monitors my mouse tracking speed is set a little higher so I can travel through the screens with ease.

But man.... can anyone explain how can I make the cursor stay in "resize" mode for more than 1 pixel at the edges/corners of windows? Thanks in advance!

---

### Post by crlang13 on 2010-03-11
Not sure if this will help, but get the compiz config settings manager from synaptic package manager (I believe you have to search for ccsm).  There may be some options in there on resizing and whatnot.

---

### Post by asmoore82 on 2010-03-11
Gnome has got you covered!
This has to be one of the best under-used features out there...

If you Alt+click anywhere on a Window you can drag to move it without having to click the titlebar specifically.
Similarly, If you Alt+MiddleClick(wheel click on modern mice), you can resize a Window.

If you Alt+RightClick, you bring up the Window Menu, just like right-clicking its titlebar.

A lot of folks, including Linus Torvalds himself, find this MiddleClick and RightClick
behavior bass-ackwards, as resizing is much more useful than the window menu.
If you wish to change this, it's easy but different depending on whether or not
you are using Compiz "Desktop Effects"

Also, the default keyboard shortcut to start resizing a Window is Alt+F8 :KS

---

### Post by mgmiller on 2010-03-11
You will also find if you just want to grab with the mouse as you have been doing, that the lower right corner of the window has a much larger active area then the sides or bottom.  It's a much easier spot to grab and it allows you to resize both horizontally and vertically at the same time.

---

### Post by keforex on 2010-03-11
Wow thanks for the super quick replies guys. While all the workarounds suggested are true and valid, I was wondering if the active area on the left and right of windows could be bigger. I do use compiz and I am somewhat familiar with gconf-editor but I don't even know if there is an option for that or if this is hard coded in linux.

The Alt-F8 solution works for now for me but it kind of slows down my work flow too, as I need to press keys.

Perhaps a solution would be having a cursor shaped as a double arrow where the active area would be the arrow stem.

---

### Post by asmoore82 on 2010-03-11
> **asmoore82 said:**
> Similarly, If you Alt+MiddleClick(wheel click on modern mice), you can resize a Window.

Just wanted to make sure that this caught your attention.

---

### Post by tgalati4 on 2010-03-11
Set your resolution to 1024x768.

---

### Post by stinkeye on 2010-03-12
You could use a window border theme with a thicker edge.
I use the polaris theme for this reason.
[**_[COLOR="DarkRed"]Polaris[/COLOR]_**]("http://www.gnome-look.org/content/show.php/Polaris?content=93896")

To change your border go to Appearances > customize > Window Border

Something else you might find useful is to position and resize windows with wmctrl.
```
sudo apt-get install wmctrl
```

I bind this code to a key in compiz commands.
```
wmctrl -r :ACTIVE: -e 0,400,250,890,560
```

wmctrl -r :ACTIVE: -e g,x,y,w,h
g    gravity (leave as 0)
x,y  the position of the top left corner of  the  window
w,h   the  width and height of the window

---

