---
title: "Numpad navigation in console under X"
date: 2010-02-12
forum: Desktop Environments
---

### Post by semargl on 2010-02-12
First of all, this is not famous problem, which solves by unchecking "Allow to control the pointer using the keyboard".

My numpad navigation does not work in console under X. Nor in Konsole/KDE/Kubuntu (9.10), nor in Console/Gnome/Ubuntu (9.04).
It works in graphics applications. It works in system console in text mode (Ctrl+Alt+F1..6) too.
But in Konsole I can't navigate cursor by numpad arrows in Midnight Commander or text editors. When NumLock is on - the numbers are typed. But when it off, nothing happens - cursor doesn't move. The same reaction from Home/End/PgUp/PgDn keys on numpad.

Please help!
I hate navigating in text console by arrows between mainpad and numpad! ](*,)

---

### Post by skief on 2011-08-01
This is quite an old post so I wonder if you have solved the problem already. I have recently had some success solving numpad problems using xmodmap. Did you try that at all?

To get started, you might use xev to see which X events are being generated when you press those keys. Maybe compare what happens when you're in a console, versus when you're in a graphics application.

---

### Post by semargl on 2011-08-01
Hi skief,

To be honest, now I don't remember how I have solved this problem :)

Anyway, thank you for advice!

---

