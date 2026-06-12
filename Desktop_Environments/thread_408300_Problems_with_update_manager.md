---
title: "Problems with update manager"
date: 2007-04-13
forum: Desktop Environments
---

### Post by DeathBri on 2007-04-13
Hello,

I'm having trouble updating my software. After I click the pop-up which informs me that I have a number of updates available, theupdate manager appears. I select which application I want updated and press install updates. In the lower panel appears a box that sais "starting administrative application" which disappears after a short while.

After this a window should appear requesting the password...but most of the times it doesn't. After the "starting administrative application" box disappears, the update manager remains grayed out and I have to close it with force quit.

Does anyobdy have the same problem, or can anyone help me fix it?

P.S. The same happens when I try toinstall a new application with Add/Remove

---

### Post by hackerssidekick on 2007-04-13
Try doing this in a terminal:
```
sudo aptitude update
sudo aptitude dist-upgrade
```

Post the result of the commands here and we'll go from there.

---

### Post by xopher on 2007-04-13
You can still update with apt-get?

```
sudo apt-get update; sudo apt-get upgrade
```

Edit: Aah, someone else beat me to it, guess this means I get to go to sleep ;)

---

### Post by excelsior on 2007-08-20
I have precisely the same problem, and apt-get still works

But I've noticed that a similar crash occurs when I try to change my timezone.

---

