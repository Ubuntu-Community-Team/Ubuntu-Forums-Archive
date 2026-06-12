---
title: "System Overload"
date: 2009-02-13
forum: General Help
---

### Post by yusuo85 on 2009-02-13
PC runs very nicely after a fresh install but after a while the computer uses up loads of its ram for no reason.
This is noticeable in VLC as the frame rate slows down, however nothing has changed. Im finding it very hard to determine why this is happening let alone solve it currently its using 70% of the cpu and thats juist running vlc with deluge in the background.
I dont know if anyone will be able to help me and sorry for the lack of info

---

### Post by Peter09 on 2009-02-13
Can you post the specification of your machine. Also its worth installing htop

```
sudo apt-get install htop
```

run htop in a terminal

```
htop
```

Are you using swap space as well as RAM, the system will naturally use as much RAM as it can, its only if its using a lot of swap space that you need to worry.

---

### Post by yusuo85 on 2009-02-13
yeah i have a 3.2ghz p4, 1.25gb ram. it should be more than sufficent not to have a probelm, also just realised it seems to use less memory when i have firefox open as well, as long as im on the firefox screen and dont have to video in the foreground

---

### Post by yusuo85 on 2009-02-13
also htop showed me that x was using over 50% of the system memory.
Swap space when i installed i gave over 600mb

---

### Post by Peter09 on 2009-02-13
Yes, but swap space is only used when the system runs out of RAM. So if you are not using much swap (bottom line on HTOP memory display) then you do not need any RAM.

---

