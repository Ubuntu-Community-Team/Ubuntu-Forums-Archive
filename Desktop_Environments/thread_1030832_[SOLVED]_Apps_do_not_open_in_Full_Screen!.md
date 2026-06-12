---
title: "[SOLVED] Apps do not open in Full Screen!"
date: 2009-01-04
forum: Desktop Environments
---

### Post by gibph on 2009-01-04
Greetings

Since a recent update, any applications opened under Gnome open unmaximized  ... I have a panel at the top of my screen which hides the max/min/close buttons.  The only way to see them is to do an alt/F10 which maximizes the current window so I can close the app.!
Where is the setting for starting apps. MAXIMIZED???!!  - can't find it anywhere!!

I would really a appreciate you help...
thanks

PG

---

### Post by gettinoriginal on 2009-01-04
First, your panel should not hide your title bar, so next time hit F11 twice, this will allow you to maximize your windows without alt F10.  Once you have maximized a window, close the browser or app and you should be back to normal.  :P

---

### Post by gibph on 2009-01-04
Thanks for the reply - but unfortunately I've tried that  and it does not work! (it USED to)...
The only way for me to see the title bar from under the panel is alt/f10!!

Cheers

PG

---

### Post by gettinoriginal on 2009-01-04
As a temporary fix, move your panel to the bottom, then open an app or browser, maximize as normal, then close it and see if it helps.  Why your panel is covering your title bar I have no idea.  You might check under "view" and make sure that "full screen" is not checked.

---

### Post by gibph on 2009-01-04
Thanks again - but .... been there/done that!!
and still the same result...
As I said,  since a recent update ( I think it was a compiz update that did it!) I must alt/f10 to see the title bar...

Let me know if you hear of the same thing or have a fix..
Cheers

PG

---

### Post by gettinoriginal on 2009-01-04
If you believe it is compiz, then try this:
```
gconftool-2 --recursive-unset -a /apps/compiz
```

It resets compiz back to all defaults, and should solve any conflicts.

---

### Post by gibph on 2009-01-04
Hey!!!
That did it!!

A huge thank you...
It had been bugging me for weeks! and it also fixed the way my mouse handles some compiz actions..

Double cheers

PG

---

### Post by gettinoriginal on 2009-01-04
Glad it got fixed, please go to tools and mark this as solved. :P

---

### Post by J Berkove on 2009-01-05
Im another user with the same problem. Tried all of the above with no success. When you sugested entering gconftool-2 --recursive-unset -a /apps/compiz I suppose you meant in the terminal window which I did. Still no change. i have to manualy strech the program downto full length or hit F11

---

### Post by gibph on 2009-01-05
Yes you enter the command in a terminal window.
It worked for me... only I'd like to know exactly where the problem was.
Try looking in the compizconfig settings manager under workarounds or try the other fixes listed above.

PG

---

### Post by gettinoriginal on 2009-01-05
J Berkove, try this, open your browser or an application, manually diminish the size, (if it is not maximized, then make it even smaller) then maximize, if it maximizes properly,  close your browser and then reopen it to see if the problem is solved  :P

---

