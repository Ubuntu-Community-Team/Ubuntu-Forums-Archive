---
title: "Keyboard binding for toggling keyboard layouts"
date: 2012-06-08
forum: Desktop Environments
---

### Post by Accidus on 2012-06-08
I have multiple keyboard layouts and I wish to toggle between them.

The obvious

System settings -> Keyboard layout -> Layouts -> Options -> Key(s) to change layout

doesn't have any effect, regardless of which option I choose.

I.e., if I tick Ctrl+Shift and then close all the menus, hitting Ctrl+Shift doesn't change the layout.

I can change the layout using setxkbdmap, though.

The issue started with the upgrade to unity (two releases ago). I am now using 12.04.

I know this is a pretty vague question, but I'm not sure what and where to check. If anyone can tell me what information I should include, I'll gladly supply that.

---

### Post by 3Miro on 2012-06-08
Alt + Shift works well for me, try it first.

My guess is that Ctrl + Shift is already set as a shortcut in Compiz/Unity to do something. Install CCSM and look at the shortcuts there, see if you can find what is assigned to Ctrl + Shift.

---

### Post by Accidus on 2012-06-09
Cheers 3Miro!

> **3Miro said:**
> Alt + Shift works well for me, try it first.

I've tried this, and it doesn't work.

> **3Miro said:**
> 
My guess is that Ctrl + Shift is already set as a shortcut in Compiz/Unity to do something. Install CCSM and look at the shortcuts there, see if you can find what is assigned to Ctrl + Shift.

Sadly, this also doesn't work. I've disabled Unity, and compiz doesn't use the combinations I've tried.

---

