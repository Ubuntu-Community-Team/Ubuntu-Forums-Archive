---
title: "Help! Window controls gone, windows won't drag!"
date: 2010-05-09
forum: Desktop Environments
---

### Post by starbase1 on 2010-05-09
Yesterday I adjusted the position of the windows controls back to what it was before, by using the configuration editor to set apps / metacity / general / button layout to "menu:minimize,maximize,close"

At the time everything seemed good, the buttons moved, and it all worked.

This morning I rebooted back into Lucid Lynx Ubuntu 64 bit, and now I find there are no controls on the windows, and I cannot even click and drag them, or double click the title bar to maximise!

I checked, and the string I altered is still the same.

I can still move windows with Alt-F7 and the mouse, and can resize by dragging out the bottom right corner.

Anyone got any ideas?

Nick

---

### Post by starbase1 on 2010-05-19
Any anyone offer suggestions for this please? 

I'll settle for a way to completely reset the window behaviour back to the defaults - as it is, Ubuntu is close to completely unusable...

Nick

---

### Post by quantumottle on 2010-07-06
Same problem here. window headers on all apps just, "<i>gone</i>". This is weird, wish someone with advice would find this post...

---

### Post by starbase1 on 2010-07-08
Thanks for bumping this - The lack of response is very depressing, and I have not booted into Ubuntu in a very long time...

---

### Post by micro777 on 2010-07-29
I've had the same problem in Lucid. You can go to Appearance and click 
Visual Affects and change to None. That returned all my windows to normal.
Hope that will help you also:-)

---

### Post by linux18 on 2010-07-29
```
sudo apt-get purge metacity && sudo apt-get clean && sudo apt-get install metacity
```
unless your using compiz then replace metacity with emerald

---

