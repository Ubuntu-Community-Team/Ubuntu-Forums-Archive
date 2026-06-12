---
title: "alt + tab help and show desktop"
date: 2007-09-04
forum: Desktop Effects &amp; Customization
---

### Post by NikoK on 2007-09-04
I noticed that the functionality is different for these two actions in ubuntu as compared to windows....does anyone know how to change the behavior of these actions to resemble windows?

---

### Post by shane2peru on 2007-09-04
> **NikoK said:**
> I noticed that the functionality is different for these two actions in ubuntu as compared to windows....does anyone know how to change the behavior of these actions to resemble windows?

Nikok, 

Actually it should work the same.  If it doesn't perhaps your keyboard is not setup correctly and the alt key is not registering.  It should work, even with Beryl installed mine still works. I mean it switches to the open applications, however it only works with the applications on that desktop that are open, so if you have an application open on another desktop, it won't switch to that (at least mine doesn't).

Shane

---

### Post by NikoK on 2007-09-04
I meant HOW it works...it doesn't work the exact same ways....for instance show desktop on windows minimizes all the windows (what I want)

and for alt tab it switched between the last 2 open windows....with ubuntu It does it some other unorganized way

---

### Post by bigboy_pdb on 2007-09-05
From what I can remember of Windows, the Ubuntu "Show Desktop" button and "ALT-TAB" work in a manner that is almost identical.

Pressing the show desktop button minimizes all of the windows. If you don't open any new windows or select any windows and you click the button again, it will put your windows in the same state that they were in before you pushed it.

When you press ALT-TAB it scrolls through the windows starting with the one that had the focus before you pressed ALT-TAB and ending with the one that hadn't had the focus for the longest time. The focus always starts on the second window (because if you didn't want to switch windows you wouldn't have pushed ALT-TAB in the first place). For example, if you open windows W1, W2, W3 and W4 (in that order) and then you press ALT-TAB, the order in the selection box will be W4, W3, W2, W1 and the focus will start off on W3. If you select W1, the new order will be: W1, W4, W3, W2 and the focus will initially be on W4.

If you minimized the windows before pressing ALT-TAB then it will use the order of focus from before the windows were minimized.

---

### Post by runagate on 2007-09-06
I had a similar problem with alt-tab as you described although I am running beryl. I found the solution in the beryl settings manager - under Window Management/Application Window Switcher/Behaviour, turn off "Switch Focus Instantly" and the alt-tab behaviour becomes more similar to the MS Windows style. If you are using metacity there may be an equivalent setting.

---

