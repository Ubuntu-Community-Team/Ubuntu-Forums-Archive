---
title: "Getting programs to run on login in Xfce"
date: 2006-03-11
forum: Desktop Environments
---

### Post by clintonthegeek on 2006-03-11
Hi Everyone!

I've just installed Xubuntu on my old Pentium III 450mhz (256mg RAM, 10gb HD) for permanent use since I cooked my laptop. :p And I must say it's working far beyond my expectations! Responsiveness is amazing.

Anyways, I've been searching around for instructions on how to get programs to launch once X and Xfce start, but am getting lots of confusing/conflicting stuff. Simply put, I want gmail-notify, kopete, and xmms to run once my desktop loads. I don't want session saving, or any of that stuff, just for these programs to load when I turn the computer on.

I've found some stuff about .xinitrc, but that hasn't been working for me, maybe I'm doing it wrong.

Any help would be greatly appreciated!

-Clinton

---

### Post by 5-HT on 2006-03-11
If you don't want to simply save a session with the wanted programs open, you could always create an 'Autostart' directory within the Desktop directory (~/Desktop/Autostart) and place any executables you want started upon XFCE boot into an executable script in that directory. 

Upon booting, XFCE will source the Autostart directory, and whichever scripts you have in there will be executed.


HTH

---

### Post by clintonthegeek on 2006-03-11
[QUOTE=5-HT]If you don't want to simply save a session with the wanted programs open, you could always create an 'Autostart' directory within the Desktop directory (~/Desktop/Autostart) and place any executables you want started upon XFCE boot into an executable script in that directory. 

Upon booting, XFCE will source the Autostart directory, and whichever scripts you have in there will be executed.


HTH[/QUOTE]

Aha! Thank you very much. :D

---

### Post by 5-HT on 2006-03-11
No prob, hope you get XFCE customized to your liking.

It's a nice, easy to use feature (I think KDE and a few WM's also support it)...albeit a little hard to figure out it exists without a little research.

If you have any problems, just post back and myself or anyone else that happens along this threat and is willing will try to work them out with you.

HTH

---

