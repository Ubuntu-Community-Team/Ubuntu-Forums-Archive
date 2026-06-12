---
title: "Unplayable frame rate without vsync"
date: 2020-04-07
forum: Gaming &amp; Leisure
---

### Post by pogoh43010 on 2020-04-07
My DE is XFCE and I have Intel graphics. Games such as Minecraft run at <5 FPS when full screen and in game v-sync is turned off. When v-sync is on, it runs at 60 FPS. What is causing this? This happens whether the compositor is on or not, the only difference being screen tearing when the compositor is off.

When played in windowed mode I get ~10 FPS independent of whether v-sync is turned on or not. Does v-sync only have an effect in full screen mode?

---

### Post by mastablasta on 2020-04-08
> **pogoh43010 said:**
> My DE is XFCE and I have Intel graphics. Games such as Minecraft run at <5 FPS when full screen and in game v-sync is turned off. When v-sync is on, it runs at 60 FPS. What is causing this? This happens whether the compositor is on or not, the only difference being screen tearing when the compositor is off.


it's a combination of monitor, GPU and game. v sync syncs games frame rate to the one available on monitor. if game works well with v-sync then just leave it on.

> 
When played in windowed mode I get ~10 FPS independent of whether v-sync is turned on or not. Does v-sync only have an effect in full screen mode?

yes and no. depending on what is going on on the desktop. but in general yes only full screen works properly. makes sense since if you use 2 different refresh rates to draw game and to draw desktop then it has to focus on one of those two, right?

---

### Post by Perfect Storm on 2020-04-08
You could try gamemode for Linux to squeeze it a bit more: [https://www.omgubuntu.co.uk/2019/08/feral-gamemode-ubuntu](https://www.omgubuntu.co.uk/2019/08/feral-gamemode-ubuntu)

---

### Post by pogoh43010 on 2020-04-08
> **mastablasta said:**
> it's a combination of monitor, GPU and game. v sync syncs games frame rate to the one available on monitor. if game works well with v-sync then just leave it on.



yes and no. depending on what is going on on the desktop. but in general yes only full screen works properly. makes sense since if you use 2 different refresh rates to draw game and to draw desktop then it has to focus on one of those two, right?

Thanks for the vsync explanation! What I'm confused about is that disabling vsync should increase FPS from what I understand. I think I might have something configured wrong, I suspect it has something to do with Intel graphics or compositing but I don't know.

---

### Post by pogoh43010 on 2020-04-08
> **Artificial Intelligence said:**
> You could try gamemode for Linux to squeeze it a bit more: [https://www.omgubuntu.co.uk/2019/08/feral-gamemode-ubuntu](https://www.omgubuntu.co.uk/2019/08/feral-gamemode-ubuntu)

Thanks, I'll check it out and hopefully it will increase performance. The game still should have a playable FPS without vsync and I am still hoping to find a fix for that.

---

### Post by mastablasta on 2020-04-09
> **pogoh43010 said:**
> Thanks for the vsync explanation! What I'm confused about is that disabling vsync should increase FPS from what I understand. I think I might have something configured wrong, I suspect it has something to do with Intel graphics or compositing but I don't know.


vsync syncs the frame rate per second (FPS) to the one on monitor. so if monitor is 60Hz, your game will be synced to work at 60 FPS. if your monitor supports 120 Hz then it will sync it to 120 FPS (if GPU is strong enough). 

eye can see about 25-30 FPS. which is why game is perfectly playable if you can achieve around 30 FPS on average. with added special effects game will look smoother on average 60 FPS. so often getting 240 FPS won't help you much in terms of what you see on screen. where the FPS is important is in competitive gaming because > "Higher frame rates do reduce input lag." and you would want to have lag in  in game like CS:GO for example where reaction times are super important. more here: [https://blurbusters.com/faq/benefits-of-frame-rate-above-refresh-rate/](https://blurbusters.com/faq/benefits-of-frame-rate-above-refresh-rate/)

but for Minecraft, i wouldn't worry too much as long as FPS is not too low (in which case you will get major lag). 60 FPS on minecraft is cosy.

---

