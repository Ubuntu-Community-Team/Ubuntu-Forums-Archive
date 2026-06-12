---
title: "Compiz problem: inactive windows are on top!"
date: 2007-10-27
forum: Desktop Environments
---

### Post by evilmonkey on 2007-10-27
Hello,

I just installed Gusty with compiz, wiping (formatting) a computer where I had Feisty with Beryl. My problem is this: when I have two windows, and I try to switch to the inactive one by just pressing on it, it becomes active, but the (newly) inactive window stays on TOP! The only way for me to get the inactive window to go away is to click on titlebar of the window that I want on top. 

This is really annoying. Furthermore, it wasn't the case when I had Beryl. I know there's a solution to this, so can anyone please point me in the right direction? Thank you. :)

---

### Post by evilmonkey on 2007-10-27
My bad I posted in the wrong forum. :( Question stands though, and if admins want to move the thread, that's cool too.

---

### Post by itsbradman on 2007-10-27
Does the inactive window become transparent?  If so, make sure that opacity isn't checked in the compiz config manager.  I had this problem, unchecked it, and everything was fine.

---

### Post by evilmonkey on 2007-10-27
Opacity? You mean Opacify? If so, it's unchecked. 
New development: it seems like I don't need even need to click on the window at the bottom to get it to activate, I can just hover my mous over it. In that window I can type, do whatever, then mouse over the window at the top, and it becomes active again, and I can type in it and do whatever. But I can't get the window at the top to disappear. This behavious with the mouse is not what I want either. I just want "normal" behaviour where I can click anywhere on the bottom window and the bottom window will jsump to the top and become active. Thanks for the help. :)

---

### Post by evilmonkey on 2007-10-27
I think I found the options that control this behaviour, they're under compizconfig->general  options->focus and raise behaviour. Most of the options there are blue (for some reason) and I need to select "raise on click" (I think). However, when I try to select it, it just unselects itself. Any ideas why?

---

### Post by evilmonkey on 2007-10-27
Okay, I got it.
This has to be fixed from KDE's properties. Go to System Settings -> WIndow Behaviour and make "Click to focus" is set as the policy.

Reference: [http://ubuntuforums.org/archive/index.php/t-503145.html](http://ubuntuforums.org/archive/index.php/t-503145.html)

---

