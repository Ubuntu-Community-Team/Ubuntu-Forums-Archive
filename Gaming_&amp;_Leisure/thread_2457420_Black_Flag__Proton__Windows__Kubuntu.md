---
title: "Black Flag / Proton / Windows / Kubuntu"
date: 2021-02-01
forum: Gaming &amp; Leisure
---

### Post by Shibblet on 2021-02-01
All of the above!

So, I have recently started playing Assassin's Creed IV: Black Flag, and it's an older game, I know.  Came out in 2013.  

There are currently some issues with this game when it is run in Windows 10.  Apparently you have to exit the game to the desktop, open up the task manager, turn off one of the CPU's for the application by setting the affinity, and the game will run smooth as silk after that.

The reason, I am told, is because the game was made for the XBox 360 originally, and it only takes advantage of two CPU cores.  So, on Windows 10, if you turn off one core, it will auto-balance it's load to the rest of your CPU cores, and run great.

I have noticed that the application does the same in Kubuntu.  Only one CPU core seems to be doing the heavy lifting.  Is there a way to "set affinity" for the application in Kubuntu?

Also, this may be a legitimate problem for many games that work in Proton / Wine, at least as far as performance is concerned.

---

### Post by CatKiller on 2021-02-01
> **Shibblet said:**
> Is there a way to "set affinity" for the application in Kubuntu?
You'll probably want to look at **taskset**.

---

