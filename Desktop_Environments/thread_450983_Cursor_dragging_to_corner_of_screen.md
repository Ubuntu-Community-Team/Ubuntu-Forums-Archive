---
title: "Cursor dragging to corner of screen"
date: 2007-05-21
forum: Desktop Environments
---

### Post by Prodigious Penguin on 2007-05-21
Hi, I'm using a Dell Latitude C610 but switched out the keyboard a couple days ago... The keyboard is from a Dell Latitude C640.  Originally, the new hardware worked fine in Windows but the cursor always "drifted" towards the bottom left corner of the screen in Dapper - I say "drifted" because it was more of a jump every half second or so - there was no smoothness to the motion like you would expect if a mouse were dragging it.

Got on the #ubuntu channel on freenode, someone suggested changing the color depth from 24 to 16 in xorg.conf since they had a similar problem with another ATI chipset.  Well, that solved the issue in Dapper.

Unfortunately, I'm having the same problem on the Feisty upgrade I did last night... changing the default color depth didn't fix it this time.  Any ideas?

---

### Post by Prodigious Penguin on 2007-06-01
Tried installing the proprietary ATI driver for xorg but it didn't seem to want to work with the Radeon Mobility chipset.

---

### Post by Prodigious Penguin on 2007-06-07
I've tried Xubuntu and Kubuntu with no success, it's definitely an xorg issue.

---

### Post by Incarnadine on 2007-06-07
I've had that problem too, but it just turned out that my mouse was going bad and I had to replace it. Maybe you should grab a mouse and replace it with yours and see if you still have that problem. I'm hoping you haven't tried this yet though because if you have then I couldn't tell you what else could be wrong.

---

### Post by Prodigious Penguin on 2007-06-09
Tried switching back to the laptop's old keyboard and it worked fine.  Also tried a different C640 keyboard, but still had the issue.

I guess xorg doesn't like a C640 keyboard/eraser cursor being in a C610, even though Windows doesn't have an issue with it (first time I've ever had windows do something better than Linux   :( ).  Guess I'll just deal with a couple keys not being there until I can get another C610 board off ebay or someplace.

---

