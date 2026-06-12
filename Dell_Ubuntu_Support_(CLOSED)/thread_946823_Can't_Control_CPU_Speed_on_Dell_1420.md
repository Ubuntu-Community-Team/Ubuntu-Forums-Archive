---
title: "Can't Control CPU Speed on Dell 1420"
date: 2008-10-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MrSootentai on 2008-10-13
I've been having quite an annoying problem.
I can't seem to control the CPU Scaling Frequency on my Dell 1420.
I have the speed applet in the gnome-panel and when I click to change the options I change it to performance, but the the CPU speed stays on 1ghz. 
When I click to set it to 1.5ghz it still stays on 1ghz.
What should I do?
I've noticed lately that sometimes (random really) when I do a cold boot the CPU's start freq. *is* 1.5ghz but after about a minute drops straight down to 1ghz.

---

### Post by ditdot on 2008-10-14
try this one in your terminal

```
sudo dpkg-reconfigure gnome-applets
```

this command will give the applets sudo privilege, and now you can change your frequency:)

---

### Post by MrSootentai on 2008-10-14
Thanks, but I did that, and still nothing. 
I get the menu, but I still can't change it.
And I know for a fact that I can change it because under Gutsy and Vista I was able to change it.

---

