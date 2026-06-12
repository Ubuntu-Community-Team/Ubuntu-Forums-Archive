---
title: "got beryl working but can't change emerald theme + ATI powerplay feature gone"
date: 2007-03-21
forum: Desktop Effects &amp; Customization
---

### Post by DonFunBuBai on 2007-03-21
Hi all:
        After 2 days of work, I finally got beryl working. I gotta admit, I don't wanna go back to Vista even though I have dual boot.

       Now that beryl is working, I can't seem to change any emerald theme. Plus the power play feature that I used to have is gone. Let me explain what I came through step by step.

1. I installed Ubuntu 6.10 (without any problem)
2, update it  with 140 something files. (done)
3. I installed graphics card driver for my mobile ATI X1600 (the one I download from ATI 8,34,8 )
4. I was able to use  these two ```
aticonfig --set-powerstate=1
``` and ```
aticonfig --list-powerstates
``` to check the status of my graphics card and adjust it's power.

5. After I gathered all the info I need to install beryl, I followed the instruction step by step. Now that beryl is working, but the powerplay feature is gone. (the only change I made to the graphics card setting was /etc/x11/xgl.conf   I change the driver name from vesa to fglrx)

Can Anyone help me with these two problems please. I did researches on many sites and forums but still couldn't find any solution

a linux noob desperate for help ^_^

thanks very much for your time

---

### Post by xopher on 2007-03-24
You realize the correct file is: /etc/X11/xorg.conf ? ;)

For the emerald problem, make sure you are using emerald as your window manager, not e.g.. Heliodor (which uses Metacity themes), this is easily changed in the beryl-manager (right click on the icon etc).

ATI, well, no idea, sorry, not my area of expertise to be frank.

---

### Post by kerneloftruth on 2007-04-03
there used to be an append-option during launch of xgl to start an additional xorg-server to xgl

[http://forums.gentoo.org/viewtopic-p-3933501.html#3933501]("http://forums.gentoo.org/viewtopic-p-3933501.html#3933501")

but this doesn't seem to work on feisty with newest xgl (>=7.2) :confused: 

> -ac -accel xv -accel glx:pbuffer -deferglyphs 16 -xorgAc &

anyone was successfl in using powerplay with feisty & xgl ?

thanks in advance :popcorn:

_**update:**_

try: 

```
DISPLAY=:0 aticonfig --lsp
```

```
DISPLAY=:0 aticonfig --set-powerstate=3
```
```
DISPLAY=:0 aticonfig --set-powerstate=1
```

this seems to work

---

### Post by onaka_the_kaka on 2007-10-19
Perfect, the "DISPLAY=:0 aticonfig --set-powerstate=1" was what I was looking for.

Maybe there should be a button for this somewhere or an automatic manager for the powerstate.

---

