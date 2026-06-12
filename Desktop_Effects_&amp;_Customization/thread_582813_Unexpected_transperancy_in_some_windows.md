---
title: "Unexpected transperancy in some windows"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by koma77 on 2007-10-20
When using desktop effects (with no transparancy effects activated) some programs are almost unusable due to them being something like 50% transparent all the time.

Example of software that does this is Eagle and Xaos...

Is that an error with those software or is it something within desktop effects?

---

### Post by jeb3518 on 2007-10-20
The only thing I can think of to do is to make sure you have the Advanced Desktop Effects manager;
```
sudo apt-get install compizconfig-settings-manager
```

...then just go through **all** the settings to make sure you didn't miss any options since some apparently seem to be redundant.  Good Luck.

 - Jeb

---

### Post by lauwe on 2007-10-22
I have noticed a similar thing with Eagle. Black things such as text seem to be transparent.

---

### Post by parts-man73 on 2008-01-21
Has anyone fixed this problem?  I have the settings manager installed. But I can't find any settings that make a difference. I am also trying to use Eagle, but no luck, I can't see the windows because they are transparent.

Brian

---

### Post by martbuang on 2008-04-01
I had the same problem with transparent text in Eagle. The way I fixed it was to disable visual effects, this work for me with 7.10. 

From the *System* menu select *Preferences>Appearance* this will give you *Appearance Preferences* window, select the *Visual Effects* tab and select the *None* option. 

Eagle should now have black text instead of transparent.

---

