---
title: "my linux (ubuntu) pc will freeze during gameplay!!! help needed"
date: 2016-10-26
forum: Gaming &amp; Leisure
---

### Post by jtsaver69 on 2016-10-26
ok so i have steam and i have a game  i play on there and i have bf1942  game also both games are very able to play on any pc i use wine btw and in the first 12 seconds it will freeze then after like 10 secs it will come back only for a sec or 2 and repeat so i need help i have skype so if we need to chat wont be a prob thats it thanks!!!
but yeah all games freeze on me but they worked like not even 3 or 4 days ago so i dont understand it

---

### Post by mastablasta on 2016-10-27
i didn't quite understand - all games freeze or only steam games?

when runnign form iwne run it form terminal see if there are any errors. 

make sure the GPU drivers that are installed are good for your chip.

---

### Post by jtsaver69 on 2016-10-27
memory 3.8 gib
processor Pentium(R) Dual-Core CPU T4400 @ 2.20GHz × 2 
graphics Mobile Intel® GM45 Express Chipset 
os type 64 bit
Disk 241.9 GB
i never knew about drivers before this what they were but now i sort of know well so i went to [software and updates] and then went to additional drivers this is what i got> Unknown: Unknown
this device is using an alternative driver using processor microcode firmwar for intel cpus fron intel-microcode (proprientary)

---

### Post by mastablasta on 2016-10-28
intel chips have drivers built into kernel.

do you actually have 3D acceleration ?
You can copy and paste this into terminal. first command Will install some tools, second one Will check if chip has 3D acceleration enabled.
```

sudo apt-get install mesa-utils
LIBGL_DEBUG=verbose glxinfo
```

as i remember it throwns out a bunch of lines. you go though them and "*Make sure your OpenGL renderer string does not say "software rasterizer" or "llvmpipe" because that would mean you have no 3D hardware acceleration*"

---

