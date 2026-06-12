---
title: "GUI Hangs"
date: 2009-02-19
forum: Desktop Environments
---

### Post by PlusFive on 2009-02-19
I believe I had found issue in Gnome. 
GUI hangs sometime when popup message appears and other window at this time become active (on focus).
Everything seems continue working , charts moving in system monitor and other programs shows it's windows ok, but I can't click on button or links like some modal window opened, but there is no modal windows in focus.
Alt+Tab didn't work. Only Alt+Ctrl+Backspace works ok and restart GDM.
Also I get such problem and able to reproduce it when I debugging java application with eclipse and set break point which stop modal opened window in AWT thread. I see in eclipse stopped breakpoint but mouse become useless.
Can anybody suggest something, or maybe I need to submit this in some other place?

Thankyou!

---

