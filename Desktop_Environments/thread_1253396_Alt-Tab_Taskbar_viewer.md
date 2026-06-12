---
title: "Alt-Tab Taskbar viewer"
date: 2009-08-30
forum: Desktop Environments
---

### Post by Tyson D on 2009-08-30
When ever i Alt-Tab a little window will show up with a little thumb nail of all possible applications, I've been wondering how to take that off, because i know my laptop doesnt do that....


im not rocking anything special, just the stock gnome/nuatilus setup, ........thoughts?

---

### Post by tgeer43 on 2009-08-30
I don't know why you'd ever want to disable ALT+TAB switching but if you insist...

Go to System->Preferences->Keyboard Shortcuts, scroll down until you see the ALT+TAB shortcut and disable it.

If your laptop doesn't have this functionality then it was disabled somehow because it is the default behavior.

tgeer

---

### Post by Copernicus1234 on 2009-08-30
I dont understand. What is it your laptop cant do? Obviously its reacting to alt-tab.

---

### Post by tgeer43 on 2009-08-30
I believe he's referring to his other computer.

tgeer

---

### Post by Tyson D on 2009-08-31
haha ok both of my computers desktop and laptop respond and switch window when i press Alt-tab but my desktop will show a thumbnail pic of each window as it does so but my laptop will remain visually uneffected as it switches windows...

hope that clears it up.

---

### Post by tgeer43 on 2009-08-31
Yes, that's a lot clearer.

If you have Compiz Fusion enabled then I have your answer.

[LIST]
[*]Go to System->Preferences->CompizConfig Settings Manager.
[*]Go down to the 'Window Management' section and click on 'Static Application Switcher'.
[*]Under the 'Bindings' tab find the 'Next Window' keybinding and disable it. Make sure you choose the one for the keyboard binding and not the mouse one (the icon on the left indicates this).
[*]Now go further down to the 'Next Window (no popup)' keybinding. Enable it and set the keybinding to ALT-TAB.
[/LIST]
That should set things straight.

tgeer

---

### Post by Tyson D on 2009-09-04
Tgeer, everything works just the way i want it. I didnt have compiz installed before, its dangerous how much freedom it gives you.

thanks

---

