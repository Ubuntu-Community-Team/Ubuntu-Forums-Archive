---
title: "Inspiron 1150 Wirelss card overheats; can't turn it off with Fn+F2"
date: 2007-09-12
forum: Dell  Ubuntu Support
---

### Post by tak1150 on 2007-09-12
I have been having an overheating problem with my laptop (my left hand got a very mild low-temp burn from it!). I have narrowed the problem down to the wireless card (AR5212 atheros, which is not the one that comes with inspiron 1150).

At work, I just have the ethernet connection and at home I use wireless. So at least at work, I'd like to turn off the wireless card.

I have tried Fn+F2 and that does not work.
I have made sure that the above feature is turned on in BIOS

Does anybody have advice for me? Thank you!

---

### Post by Monkey_Tales on 2007-09-12
You can try to switch off the wireless network in the networkmanager icon  on the panel above in the screen.

---

### Post by tak1150 on 2007-09-13
Thanks for replying.

Yes, that would "disable it" but the wireless card is still on after I do that (or so I think), because I can
```

wlist scan
```
and it still tells me that I am detecting wireless signals and also after I "disable" with Network-manager, the wireless card is still extremely hot.

---

### Post by tak1150 on 2007-09-19
I've also tried
```

sudo ifdown ath0
```

It is still pretty hot! Anybody?? Thanks!

---

### Post by jongkind on 2007-09-21
Wild guess: I never checked it, but can you switch it off via your BIOS?

---

### Post by tak1150 on 2007-09-21
Yes, I have the option to turn it off in the BIOS setting.
I didn't want to turn it on and off in the BIOS every time when I go to my office (ethernet) and come home (wireless). Maybe I'm too greedy, but since I know you can do it in Windows through the Dell tool thingy, I'm sure that there is a way to turn it off in Ubuntu somehow.

Meanwhile, I found an imperfect solution. I destroyed an aluminum pan that I bought at a 99 cents store and tore a piece out of the handle. Then I hammered it until it was totally flat. I then shoved the thing (plate now) on top of the wireless card and closed the lid (it was very tight). It is now spreading the heat a bit more than before and the heat on my left hand is bearable. But the heat is definitely still there :(

I'll try to post the picture of this not-so-genius invention soon!

---

