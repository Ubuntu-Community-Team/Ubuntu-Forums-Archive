---
title: "Compiz-Fusion &quot;minimize&quot; animation stuck on fade; config won't work"
date: 2007-08-07
forum: Desktop Effects &amp; Customization
---

### Post by ddumanis on 2007-08-07
No matter what I do or how I tweak the animation panel of Compiz-Config, the animation for "minimize" is stuck on Fade.

Any solutions/ideas are welcome! I have an ATI card if it matters. All other parts of Compiz Fusion seem to work fine.

---

### Post by hyperair on 2007-08-07
Delete your .compizconfig directory, and reconfigure from scratch. Use the flat-file backend. That's more stable.

---

### Post by kholsheimer on 2007-08-09
I have a similar problem (and I am already using the flat-file backend).

I wish to change the duration of the magic lamp animation on both minimizing and unminimizing, However, the change is only applied to *un*minimizing; the minimizing effect is still as quick as before. Also, in addition to this problem, the minimizing effect also fades on top of 'magic lamping'.

Is there  some way to change this or is this an actual bug?

Thanks.

---

### Post by hyperair on 2007-08-11
Actually no. You must delete your .compizconfig folder. There's some problem porting old preferences to the new versions. By deleting the .compizconfig folder you'll have reset your preferences, and you won't experience any problems.

---

### Post by coldstatue on 2007-08-30
Deleting the folder and reconfiguring did not fix my problem. I was already using flat-file. I was wondering why restoring from a minimized window produced an effect, but minimizing produced no effect. Then, I tried burn as the minimize effect. It works great on maximize, but the window just disappears on minimize, leaving the flames falling in space - no window. So it seems that the window is being taken off of the screen before the effects can be implemented on it.

---

### Post by coldstatue on 2007-08-30
There is a new plugin in the effects section called "Fading Windows". Turn it off

---

