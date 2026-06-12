---
title: "Few indicators are missing"
date: 2010-05-18
forum: Desktop Environments
---

### Post by Thrashard on 2010-05-18
Hi, i have pressed "Remove from panel" on keyboard indicator from the top toolbar with will to add it on the lower one. It has disappeared along with network connections. They're missing in the "Add to panel" list. Thanx for help. I am using ubuntu 10.04. There are no problems in older versions.

---

### Post by Thrashard on 2010-05-19
Up!

---

### Post by Dkkline on 2010-05-19
yet another indicator applet remove, :)

Had the same problem,

here is how it should be done:




RIGHT CLICK where you want it click "add to panel" then find "Indicator Applet" and click! 

now you should get your sound icon + universal acces + mailing icon

if you want to remove universal acces, don't right click and say remove from panel, instead do this:

1.) click "ALT + F2" (you should get a little box up saying "run application") type
Code:
gnome-keyboard-properties
ENTER
2.) A window saying "keyboard Preferences" should just had popped up, choose the tab "Accessibility" and uncheck the box saying "Accessibility features can be toggled with keyboard shortcuts".
3.) Log out and Log in, or restart, and TAADAAA


hope this helps, cheers

---

### Post by Dkkline on 2010-05-19
try this






RIGHT CLICK where you want it click "add to panel" then find "Indicator Applet" and click! 

now you should get your sound icon + universal acces + mailing icon

if you want to remove universal acces, don't right click and say remove from panel, instead do this:

1.) click "ALT + F2" (you should get a little box up saying "run application") type
Code:
gnome-keyboard-properties
ENTER
2.) A window saying "keyboard Preferences" should just had popped up, choose the tab "Accessibility" and uncheck the box saying "Accessibility features can be toggled with keyboard shortcuts".
3.) Log out and Log in, or restart, and TAADAAA


Cheers, the thing is it's something called indicator applet, it have a diffrent icon under "Add to panel"


EDIT: seems it came out twice..., very strange... sorry about double output!

---

### Post by Thrashard on 2010-05-19
It didn't help me. I've got only sound/mail applet now but there's no keyboard indicator.

EDIT: I have realised that in 10.04 keyboard indicator is included in the notification area. That sucks.

---

