---
title: "too-tall windows on a netbook (classic desktop)"
date: 2009-07-27
forum: Desktop Environments
---

### Post by bandofmercy on 2009-07-27
my question is pretty straightforward i guess.  i have a netbook running classic desktop mode (compiz enabled) and i'd like a fix, or at least a workaround, for a problem i'm sure many people have had.

when a dialog box is too big to fit in the screen vertically, it can be hard to click ok, close or even see all the options.  if you maximize it it may still not fit and although it takes up the whole screen it will bounce to the upper and lower limits of the window when you try to click.  i've had limited success with either holding the click down and then moving back to where the button has moved or using maximumize in compiz to force windows smaller, but like i said... minimal success.  thanks in advance for any help!

---

### Post by komputes on 2009-07-27
Alt-click-drag will allow you to grab a window from any point making it easy for small screens to access OK buttons at the bottom of a large dialog. :D

If you find that the dialog cannot pass the top delimiter (it blocks at that point) you can turn off that delimiter by running the following command:

```
#==========
#How to have an unconstrained windows to the top of the screen
#==========

$ gconftool-2 --set /apps/compiz/plugins/move/allscreens/options/constrain_y --type bool 0    

```

---

