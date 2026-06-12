---
title: "Bad actual display dimensions with i810"
date: 2005-10-23
forum: Desktop Environments
---

### Post by Mataanin on 2005-10-23
Hello,

I upgraded from hoary to breezy today. After I restarted, I have noticed that actual display (the area on the monitor screen that actually shows something) width has shrinked.

My xorg.conf didnt give me any clue for it. Xorg.0.log said that the area should be 320x240 mm, but it is actually around 290x240. 

Do anybody have any ideas?
My card is integrated "Intel i810 video" and monitor "SyncMaster 765MB"

xorg.conf and Xorg.0.log are attached

---

### Post by Mataanin on 2005-10-23
adding full xorg.log

---

### Post by Zeroedout on 2005-10-23
[quote=Mataanin]Hello,

I upgraded from hoary to breezy today. After I restarted, I have noticed that actual display (the area on the monitor screen that actually shows something) width has shrinked.

My xorg.conf didnt give me any clue for it. Xorg.0.log said that the area should be 320x240 mm, but it is actually around 290x240. 

Do anybody have any ideas?
My card is integrated "Intel i810 video" and monitor "SyncMaster 765MB"

xorg.conf and Xorg.0.log are attached[/quote]

normally what i had to do was put the "DisplaySize x y" in my monitor section. If you look in your moniters manual, look for the actualy screen size and put that in, that's what did it for me. here is my monitor section
Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   30 - 70
    VertRefresh 50 - 150
    DisplaySize 324 244
    Option "DPMS"

so just add the Display size of your monitor and you should be fine.

---

