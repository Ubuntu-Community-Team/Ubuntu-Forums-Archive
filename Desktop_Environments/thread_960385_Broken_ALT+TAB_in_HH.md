---
title: "Broken ALT+TAB in HH"
date: 2008-10-27
forum: Desktop Environments
---

### Post by realn on 2008-10-27
Configuration = Kubuntu HH 8.04
In keyboard shortcuts I have ALT+TAB assign to "walk through windows" action and ALT+SHIFT+TAB to "walk through windows (reverse)".
Let's say I have 5 windows on desktop1.
If I press only once ALT+TAB I go from current window (window1) to next window (window2). I press once more ALT+TAB : surprise - I go from window2 back to window1).
If I do the same thing but with ALT+SHIFT+TAB I correctly go through all windows (from window5 to window4 ... down to window1).
It seems like a bug to me. Can you confirm, please, cause I couldn't find it reported anywhere.

thanks a bunch

---

### Post by realn on 2008-10-28
It might seem a minor thing, but it's quite annoying once you have this.

---

### Post by realn on 2008-10-31
I confirm that the same thing happens in compiz, when setting up a mouse binding for the "next window" action. Thanks to anyone who can help me fix this annoying thing.

---

### Post by ee19921 on 2008-11-20
> **realn said:**
> I confirm that the same thing happens in compiz, when setting up a mouse binding for the "next window" action. Thanks to anyone who can help me fix this annoying thing.

My [keyboard shortcuts are a big mess]("http://ubuntuforums.org/showthread.php?p=6218860") now. Now, this thing also started annoying me.

---

### Post by Farmer of Bricks on 2009-01-27
> **realn said:**
> 
Let's say I have 5 windows on desktop1.
If I press only once ALT+TAB I go from current window (window1) to next window (window2). I press once more ALT+TAB : surprise - I go from window2 back to window1).

Think of your windows as a stack of cards, numbered 1-5.
Pressing Alt+Tab pulls the second card from the stack and places it on top of the deck. The cards are now renumbered to reflect their current positions. When you press Alt+Tab again, you're just pulling the second card from the stack and placing it on top. 
Confused yet?
If you want to pull the *third* card from the stack, press and *hold* Alt and press Tab twice. The holding of Tab tells the computer that you're still in the window-switcher, so it now interprets the second Tab push as an instruction to go to the next window down in the stack.

Does it make sense?

---

### Post by realn on 2009-09-10
Hi, thanks a lot for your explanation. Well, it makes sense, except that this is not what I want. What I want is to go to the third window in the list by ALT+TAB+TAB with NO reordering of the windows, so that when I press another ALT+TAB go to the fourth window in the list.

 So, here is how it's done:

[http://ubuntuforums.org/showthread.php?t=597209](http://ubuntuforums.org/showthread.php?t=597209)

Simply change in ~/.kde/share/config/kwinrc

the line 

AltTabStyle=KDE

into 
AltTabStyle=CDE

Apparently this can be done by unchecking the "show windows list" in windows behavior, but I find it STUPID (I apologize for my sincerity). Displaying (or not) the windows list SHOULD have nothing to do with the navigation scheme through that list.
So, my next question, how can I have the CDE style and still having the windows list displayed?

 Thanks a lot!

---

### Post by realn on 2010-07-20
Marked as solved.

---

