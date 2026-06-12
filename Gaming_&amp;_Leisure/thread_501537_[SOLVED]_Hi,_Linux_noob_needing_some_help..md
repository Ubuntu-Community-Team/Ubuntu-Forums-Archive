---
title: "[SOLVED] Hi, Linux noob needing some help."
date: 2007-07-15
forum: Gaming &amp; Leisure
---

### Post by bmanstyles on 2007-07-15
I need some help. I was able to get all the programs I want, like Blender and bluefish, and also Nvu. I need videogames though. I heard that the game, kobodeluxe is pretty good, so i got the download in .gz format. I extracted it, and I do not know what to do from there. Do I have to compile it? What do I have to do? Any help would be appreciated.

---

### Post by Wiebelhaus on 2007-07-15
you should be able to find the launcher and launch it , but yo , it's in the repositories so delete that package and let Ubuntu do the work.

---

### Post by cogadh on 2007-07-15
Don't bother with the tar.gz file, the game is already in the Ubuntu repositories. Just run this in a terminal:
```
sudo apt-get install kobodeluxe
```

---

### Post by Jermski on 2007-07-15
You can use the synaptic package manager that installs with Ubuntu to select games. The installations are automatic, so there is no compilation needed. I recommend ArmageTron Advanced. With Wine you can play games like World of Warcraft, or other games for the Windows platform.

---

### Post by bmanstyles on 2007-07-15
brett@brett-desktop:~$ sudo apt-get install kobodeluxe
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kobodeluxe


this is the error message i got, i dont know what ubuntu im running, but apparently it cannot find the package.

---

### Post by cogadh on 2007-07-15
You probably don't have the universe repositories enabled. Start Synaptic Package Manager and click on Settings > Repositories. Then check the universe entry, then run this:
```
sudo apt-get update
sudo apt-get install kobodeluxe
```
Or, you can just install the game through Synaptic as Jermski suggested.

---

### Post by bmanstyles on 2007-07-15
thanks, i will  try that and let u guys know how it goes.

---

### Post by bmanstyles on 2007-07-15
it went very well, thank you.

---

