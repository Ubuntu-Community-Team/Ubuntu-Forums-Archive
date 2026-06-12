---
title: "Nautilus windows get stuck in full screen mode"
date: 2008-01-10
forum: Desktop Environments
---

### Post by Dasani on 2008-01-10
Hi,
I'm some what new to ubuntu, and I've had to make a few changes to my computing habits (like the lack of GOM player in linux!!!) but I've made them.

One thing though that is very very annoying is that since recently, some of my nautilus windows open only in a 'full screen' mode. Meaning that it covers my main panel, including the main menu, the windows list etc etc....
It is so adamant to stay there that it even doesn't let any messages (errors, transfers, or others) be seen, even if they are from the same winow! I have to hit alt+tab to use other windows, and alt+f4 to exit that windows. 
This does not happen to all folders, only to some, but I am certain that it is not some setting I have made because what folders it happens to is not consistent. For example, sometimes the Video folder under my username opens fine, at other times it does not.

I have kubuntu installed on my ubuntu, though I still use a Gnome interface (from the login menu). This is something very annoying, and none of the other messages where this subject was brought up answered the question. So perhaps the mods and the pros would like to give this another shot.

Any help would be appreciated,
thanks.

---

### Post by EnvisiblePenguin on 2008-01-23
I had the same problem when my xserver crashed. What worked for me was to run nautilus in a terminal with the --geometry=GEOMETRY_VALUE 

So what I typed was "nautilus --geometry=100x200" which makes it really small but you can resize it normally. After doing this it should restart as whatever you resize it to. Also, make sure there isn't any nautilus windows up before, it may not save it if the last nautilus window that closes is in the full screen state.

---

### Post by -siGGi- on 2008-04-05
thx i was looking to find a fix and your command has helped =)

---

### Post by enigmaniac23 on 2008-04-09
Thanks!  I just had this same problem, and this fixed it.

---

### Post by suarez.duek on 2008-07-23
> **EnvisiblePenguin said:**
> I had the same problem when my xserver crashed. What worked for me was to run nautilus in a terminal with the --geometry=GEOMETRY_VALUE 

So what I typed was "nautilus --geometry=100x200" which makes it really small but you can resize it normally. After doing this it should restart as whatever you resize it to. Also, make sure there isn't any nautilus windows up before, it may not save it if the last nautilus window that closes is in the full screen state.
Finally the solution!!! You saved me!!! that really helped~!

---

