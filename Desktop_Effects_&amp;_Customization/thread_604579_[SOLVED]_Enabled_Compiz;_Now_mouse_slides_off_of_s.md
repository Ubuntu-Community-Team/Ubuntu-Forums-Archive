---
title: "[SOLVED] Enabled Compiz; Now mouse slides off of scroll bar."
date: 2007-11-06
forum: Desktop Effects &amp; Customization
---

### Post by discmaster on 2007-11-06
I notice now that I have started using Compiz, the mouse pointer "slides off" of the scroll bar when I move it to the edge of the screen. The window is maximized. Any way around this problem/minor inconvenience? :(

---

### Post by Dr Small on 2007-11-06
Any chance you could show us a screenshot ?

---

### Post by discmaster on 2007-11-06
I could, but I don't know what that would tell you? When I move the mouse the whole way over to the right of the browser window, to scroll the page up/down, it slides past the scroll bar, off of it; Normally, it would stop on the scroll bar, in other words, isn't able to go past it.

... Now I also noticed that the Desk 1,2,3,4 blocks in the lower right corner do not display what is in each block as the did in 7.04 when I used Beryl; Is this a "Beryl only" feature? It would show if you had a browser window open on each desktop. Now there is no way to know without actually clicking on each one?

---

### Post by discmaster on 2007-11-06
I notice if I set Visual Effects to "Extra", the mouse/scrolling problem goes away; I still have wobbly windows & some other features, but now I lose "Ctrl + Alt" to rotate the desktop. :(

Any way to fix? It would be nice to have all features! :popcorn:

---

### Post by SomeGuyDude on 2007-11-06
I'm not sure how to fix this, but just for clarification for anyone who can, do you mean that with a maximized browser window, the cursor goes sort of "off the map" when you go all the way to the side?

---

### Post by discmaster on 2007-11-06
> I'm not sure how to fix this, but just for clarification for anyone who can, do you mean that with a maximized browser window, the cursor goes sort of "off the map" when you go all the way to the side?Yes, that's it. The cursor goes "off the map" when moving the whole way over to the right at any time, but without the effect enabled, you are able to basically "throw the cursor" quickly over to the side of the page & the cursor will still stay on the scroll bar.

In fact, the bar "lights up" when you mouse over it normally, but as I said, with the effects enabled, you actually end up moving too far & end up sliding off of it if you are not careful...as mentioned, a minor annoyance, would be nice to fix. :)

---

### Post by discmaster on 2007-11-06
The _mouse off the scrollbar problem_ is happening when I enable "rotate cube". If I leave that disabled, it works okay. Not a fix really, but at least I know what is causing the problem. If there is a solution where I can have both, please post!

---

### Post by swoll1980 on 2007-11-06
install compiz config go to general>general there is a option called unredirect fullscreen windows try un-checking it not sure if this will help you, but it's worth a try

---

### Post by michaelzap on 2007-11-06
I had a problem that might be similar to yours. When I would try to resize windows it was extremely difficult to grab the corners or borders (it just kind of slid off the side of the window instead of grabbing it). I found that enabling the Resize Windows plugin fixed this for me (in my Compiz config window it's all the way at the bottom in Uncategorized).

---

### Post by psyopper on 2007-11-06
I think I understand what the problem is, but let me explain it in my own words to make sure I understand...

When you have a browser window (or any window) maximized to full screen and you "throw" the mouse fully to the right you expect the mouse to be bound to the (right) edge of the screen. What is happening is that you are throwing your mouse to the right edge of the screen but the mouse rolls the cube over to the desktop to the right instead of being constrained.

If this is correct there is a solution. What you are experiencing is a setting called "Edge Flip Pointer" that allows you to flip cube sides with the mouse. To disable this you need to install CompizConfig Settings Manager:

```
sudo aptitude install compizconfig-settings-manager
```

Once installed you can access it through the System - Preferences - CompizConfig Settings Manager icon.

You are looking for a plugin called Rotate Cube in the Desktop section of CCSM. On the General tab uncheck the box marked "Edge Flip Pointer".

---

### Post by discmaster on 2007-11-06
psyopper; I believe that is what you are describing; I will try what you suggested; I also want to mention - not really pert. to this situation...but on my xp pc; If I use any firefox theme other than the original, I experience the same (unbound mouse pointer" condition. :confused:

---

### Post by discmaster on 2008-04-03
>Sigh< Well here we go again... I had a couple of crashes over the last couple days, don't know from what. Anyway, after crash/reboot, root filesystem went thru & *fixed* things that were broken, so it told me. 

After that, I noticed that when I would mouse over a folder, I would not get the "hand" pointer. Well, I was able to fix that, but now I have the initial problem of this thread; That is, that the mouse pointer slides past the scroll bar on the right side when I am on a webpage, etc. 


In other words, the pointer will not stay stop at the scroll bar, but will slide past it; I have to consciously place the pointer on the bar in order to use it. No desktop effects are enabled. I quit using them because of conflicts with openoffice/other programs.

Is there a fix for this?

It is almost impossible to browse or get anything accomplished with this crazy mouse pointer behavior. :frown:

Thanks guys!

---

### Post by discmaster on 2008-04-03
Update: I have since realized that this behavior is occurring "system wide", meaning when I open explorer windows or anything. I have been thru all the system options that I can find, appearance settings, advanced desktop settings, & just cannot find a solution.

Surely others have experienced this problem. I can't find a remedy on google or anywhere. This is really a baffling one! I'm open to any ideas at all. Please help, give me something to look for, point me in a direction for a solution - anything! :popcorn:

---

### Post by discmaster on 2008-04-03
SOLVED! 

At least in my case, a "workaround" ... System>Preferences>Appearance. Different themes have different thickness borders, some have none. That was my problem.  After the crash, a different theme loaded, one with borders, & that is why the mouse was traveling past the scrollbar to the outer window border.

Now, if I would want to use a custom theme, I guess I am stuck on that one, because the mouse will then again not stop at the scrollbar, but go past to the edge of the window border. Oh well, not perfect, but it does work.

Maybe this will shed some light for others that may experience the same issue.

---

