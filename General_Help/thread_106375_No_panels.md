---
title: "No panels?"
date: 2005-12-20
forum: General Help
---

### Post by Helljumper on 2005-12-20
Ok, I am wierded out. Ok, when I booted Linux today everything seemed fine. Then, my dad booted Windows XP and still fine. After he shuts down the computer, a few min later, I turn it on and boot Linux. When I finish signing in, I get these error messages. I don't remember what they said, but now my panel that has my windows (bottom)  and the squarer (bottom-right corner) are gone. And, everything seems to have been slown down and Linux keeps on freezing and I have to do a force shut down (holding the button) because it doesn't respond. Can anyone help? :(

---

### Post by BathroomNinja on 2005-12-20
Your going to hate this answer.

Grab some paper and a pen, reboot and write down the error messages, or as much of them as you can.  Post them here.  Also, do you know if your dad did any partitioning?  How long have you been running Ubuntu?

---

### Post by Helljumper on 2005-12-20
Your going to hate me now.

No error messages came up. At all. The first time they stopped working, the messages came up, but they don't come up now. No, my dad didn't do any partioning, because all he does is go onto firefox and listen to music. And, I have been running Unbuntu for 2-3 weeks now.

---

### Post by BathroomNinja on 2005-12-20
OK.  Is the problem still happening?  Do you still not have a toolbar?

---

### Post by Gandalf on 2005-12-20
Have you tried to do a killall gnome-panel or gnome-panel using a Terminal? I guess you can't run a Terminal since you have no panels, so do it by a real Terminal ( Ctrl + Alt + F1, press Ctrl + Alt + F7 to get back to X)

---

### Post by Helljumper on 2005-12-20
Yes, there are still errors. And to the guy who said to put the "killall Gnome-something.." Is that the only thing I enter?

---

### Post by Gandalf on 2005-12-20
try:
killall gnome-panel 

if nothing showed up, run again
gnome-panel &

---

### Post by Helljumper on 2005-12-20
Ok, I did both of those things and they didn't work. Though, on the last one it said. "I've detected a panel is already running so I will exit". That is word for word.

---

### Post by Helljumper on 2005-12-21
I know this is probably not allowed but this is really getting annoying. Not only are the panels gone (the top-left ones are still there and the time) but now my computer keeps on freezing. I feel like I am back on Windows ME :confused: I will have 4 aim windows up and 1 regular screen and it will just stop working =/ Please help me..

---

### Post by codejunkie on 2005-12-21
before you login try clicking on session and choose Failsafe Gnome and login under the failsafe session if everything is working normaly do this open a terminal and enter this
```
rm ~/.gnome2/session
```
logout and login normally.

---

### Post by Helljumper on 2005-12-21
God Hates me...

Nope, the failsafe Gnome start-up didn't work either :(

---

