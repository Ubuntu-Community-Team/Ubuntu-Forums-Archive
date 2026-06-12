---
title: "Firefox page up, page down, home, end not working"
date: 2009-01-13
forum: General Help
---

### Post by joker77 on 2009-01-13
Since today, I found that I am unable to navigate within web pages using the above mentioned keys. 

Sometimes Ctrl-Home and Ctrl-End work. 

Also space and Shift-Space work. 

The problematic keys are working in other applications eg OOO and gedit. 

Wondering if the fault occured after my (scheduled weekly) update about 36 hours ago. Anybody else with the same problem? (couldn't find any similar notifications on google or ubuntuforums) Looking forward to any suggestions/ explanations. 

Intrepid. FF 3.05.

---

### Post by Zarius on 2009-01-20
Howdy,

I had this problem too, under both Ubuntu and Windows versions of Firefox.  Just discovered that my problem was caused by being in "Caret Mode" (and then only sometimes) - you could try toggling it on/off with F7 and see if that fixes it.

--Zar

---

### Post by dchky on 2009-02-26
And for anyone like me wondering "WTF firefox has carrots now?" :-)

This is pretty easy to fix. Edit -> Preferences -> Advanced -> General tab

Uncheck "Always use the cursor keys to navigate within pages", close all your windows, and everything will be back to normal.

More info here:
[http://kb.mozillazine.org/Accessibility.browsewithcaret](http://kb.mozillazine.org/Accessibility.browsewithcaret)

---

### Post by mbeach on 2009-03-12
thank you.

---

### Post by Neo_The_User on 2009-03-12
I get this exact same problem when I compile a kernel with "Configure for small system" on and I deselect compile with exported symbols / debugging or whatever and I deselect ()BUG support or whatever.

---

