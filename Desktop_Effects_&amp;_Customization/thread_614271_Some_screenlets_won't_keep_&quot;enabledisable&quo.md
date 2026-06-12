---
title: "Some screenlets won't keep &quot;enable/disable&quot; checked"
date: 2007-11-15
forum: Desktop Effects &amp; Customization
---

### Post by dmber on 2007-11-15
I have certain screenlets (calendar, facebook, and calculator) that maintain the "automatically start on login" checkmark, but the "enable/disable" check does not stay.  i've tried deleting then trying over with the screenlet but it doesn't work.

any ideas on how to remedy this?  a good number of them work just fine.

---

### Post by mattchess on 2007-11-16
I am having the same problem...have not figured out what the fix is yet

---

### Post by jhoe on 2007-12-11
Have you tried actually removing the screenlet from the directory it was installed?  I had that problem, I removed it from the drive and rename the directory it was installed to a different name.  Ex. "Calc" might have been the original directory, deleted it, then tried "calculator" instead.

Now I am having trouble with the calculator numbers being doubled when I press a number so it might not be the best of advice ;).  I can however click the numbers to calculate something, just not type them on the keyboard.

---

### Post by rhetoric on 2007-12-24
I am having the same problem with double keyboard input in calc (and convert) but NOT in notes curiously. I am also having the problem loading Calc at startup (I have to check enable each time and it works fine, but won't load at startup GRRR!)

---

### Post by rhetoric on 2007-12-24
SOLVED: I was able to get Calc to start properly by changing the file permissions of CalcScreenlet.py to allow it to be executed as a program. For some reason this was not previously set, which explains alot.

---

### Post by dmber on 2007-12-28
that worked for me!!

thank you so much!

---

