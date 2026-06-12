---
title: "wow on previous instal"
date: 2007-09-01
forum: Gaming &amp; Leisure
---

### Post by TheFlamingBush on 2007-09-01
I have WOW previously installed on an xp partition, i decided when i installed ubuntu to partition my harddisc up to three partitions with a shared fat32 partition called e, that holds files that i share between xp and linux. 

i installed wow in xp on this partition, not the c main partition, and want to be able to run it with wine. 

I have the newest version of wine installed, on a toshiba laptop and im running dapper, as i like it and it is supported, and havent managed to change since i first got Ubuntu. 

can i run WOW through wine from this location on Ubuntu?.........ive also renamed this partition does that matter?

would really like to run through Ubuntu and allow myself the freedom to get away from using my xp partition. 

Thankyou!

---

### Post by TheFlamingBush on 2007-09-01
do i need to re-instal WOW....on linux for this to work or can i use this previous instal?

---

### Post by Nehvrook on 2007-09-02
You can use the previous install. And it should be as simple as just typing 

"wine /media/disk/Program Files/WorldofWarcraft/wow.exe" into the terminal (Obviously replacing the location of the WoW exe with your actual location)

You will probably need to edit some temp files in your WoW directory to get the best results in linux. There are a LOT of threads on WoW here so just use the search and you'll be fine

---

### Post by ministoat on 2007-09-02
i've copied it over form my old WoW folder from the windows folder to the wine programs file and its worked ok..lost about 30fps in the process but its playable

---

### Post by Nehvrook on 2007-09-03
Add

```
SET gxApi "OpenGL"
```

to your /worldofwarcraft/WTF/config.wtf

If you haven't already, that should increase performance a lot.

---

