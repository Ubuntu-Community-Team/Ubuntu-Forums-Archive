---
title: "SiS Graphics Card"
date: 2006-07-13
forum: Desktop Environments
---

### Post by Aurdal on 2006-07-13
Hey, I had to take out my nVidia card and use my onboard vga card. (The nVidia card kind of stopped the air flow in the box... :s)

Anyway, when I configure the xserver to use the sis driver, I get flarring lines running down my screen with about 1 inch between them. And when I use the vesa driver, it will only let me use the 1280 x 1024 screen resolution. This would've been fine if I didn't have an old CRT which will only give me 60hz at that resolution.

So, my question to you guys is: Which driver should I try to use? (Can anyone post a list of all the ones which comes with the xserver so I can try them all?)

Thanks
-Aurdal

---

### Post by Paerez on 2006-07-13
try:
```
# sudo dpkg-reconfigure -phigh xserver-xorg
```

That will let you reconfigure the graphics in a (kind of) friendly way.

---

### Post by Aurdal on 2006-07-13
Yeah, I like editing the file better actually... :p 

But that was a list of drivers. Thanks. :)

---

### Post by Paerez on 2006-07-13
"sis" is a driver, so you can put that in and it should work.

---

### Post by Aurdal on 2006-07-13
I am using that, but it acts weird. in 1152x864 it has flarring vertical lines trough my screen about 1 inch apart. In anything less than that anything which is semi-transparent, takes on the inverted color of what's behind it.

EDIT, the flarring lines are there in 1024x768 too, but they're _much_ less noticable. :)

---

### Post by Paerez on 2006-07-13
do you have a section like this in your xorg.conf's monitor section?
```

        HorizSync    31.5 - 94.0
        VertRefresh  50.0 - 90.0

```
try removing that. Also remove any of the "modelines" stuff down at the bottom of the file with the resolutions. Maybe its a refresh rate problem.

---

### Post by Teroedni on 2006-07-13
The Sis graphics unfortunally yields very poor performance in Linux


Her is more info about The sis graphics. Using that site you may be able to improve the Performance

[http://www.winischhofer.at/linuxsisvga.shtml](http://www.winischhofer.at/linuxsisvga.shtml)


Her is a liitle quote from the sites regarding the 760 graphic capabilities

> My advice: Don't buy a machine with a SiS760 unless this machine has dedicated local video memory. And please don't complain about "driver bugs" if you see "flashing lines" on the screen; these are the typical effects of a bandwidth problem and unavoidable - even the Windows driver can't do better. In such cases, reduce the resolution and/or refresh rate and/or color depth, or use one output (CRT1 or CRT2) only. Sorry, can't help it. There is no driver bug involved.

---

### Post by Aurdal on 2006-07-13
Thanks guys... Guess I should start looking for a new computer. :p

---

