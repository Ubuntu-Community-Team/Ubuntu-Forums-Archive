---
title: "weird desktop graphics problem"
date: 2009-07-09
forum: Desktop Environments
---

### Post by dannyboy79 on 2009-07-09
i don't know what's going on. I have a 1280x1024 desktop on screen 0 and a 1024x768 on screen 1. My main screen has a weird bar down the right side. I have run nvidia-settings multiple times, and tried to adjust my monitor but it won't go away. It happened after I tried to setup compiz and then realized that with my 2 x screens, I can't accomplish compiz. Can someone help me troubleshoot the problem? Here's a screen grab. I have a Mythbuntu theme and the main Jaunty Desktop background picture. I am running a Nvidia 6200 128mb memory with Nvidia 180 driver.

[[IMG]http://img127.imageshack.us/img127/442/weirddesktopissue.png[/IMG]](http://img127.imageshack.us/my.php?image=weirddesktopissue.png)

---

### Post by rainwalker on 2009-07-09
What happens if you change the background on your top and bottom panels?

---

### Post by dannyboy79 on 2009-07-10
> **rainwalker said:**
> What happens if you change the background on your top and bottom panels?

by merely changing the backgrounds color on the top and bottom panel nothing is affected. I have tried changing the desktop background picture and that doesn't fix it either. It's a very strange problem. It's like the top and bottom panel know that the area should be 1280x1024 but the desktop pic doesn't know any better? Also, my conky is getting cut off. Any help would be appreciated.

---

### Post by gradinaruvasile on 2009-07-10
Do u have a vertical panel on the right side?

---

### Post by dannyboy79 on 2009-07-11
> **gradinaruvasile said:**
> Do u have a vertical panel on the right side?

HAH, that was it. It didn't look like a panel so I never bothered clicking on it to try to delete it. I don't even know how it got created? Anyway, I can't believe how stupid that was. It's great to come here and get help despite how trivial it may seem. Sometimes it's just good to have others think of things because I am thinking it's way more complicated than it really is. THANKS!

---

### Post by dannyboy79 on 2009-07-11
> **gradinaruvasile said:**
> Do u have a vertical panel on the right side?

HAH, that was it. It didn't look like a panel so I never bothered clicking on it to try to delete it. I don't even know how it got created? Anyway, I can't believe how stupid that was. It's great to come here and get help despite how trivial it may seem. Sometimes it's just good to have others think of things because I am thinking it's way more complicated than it really is. THANKS!

---

### Post by rocketflame on 2009-07-11
> It happened after I tried to setup compiz and then realized that with my 2 x screens, I can't accomplish compiz

I have 2 monitors, i can still run compiz fine

did you try 

```
sudo apt-get install simple-ccsm
```

---

