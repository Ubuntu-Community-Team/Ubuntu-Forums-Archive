---
title: "PCSX MemoryCard problems"
date: 2012-02-08
forum: Emulators
---

### Post by kriltos on 2012-02-08
PCSX works like a dream but when i go to save ingame it cant see any  memory cards. Have Formatted them before use, still nothing. Also have tried creating a memory card image in HOME for permissions. pretty  annoying having to watch FF8 intro over and over to check to see if it  worked :/

Anyone got a solution ?


P.s i got limited knowledge with Terminal.

---

### Post by kriltos on 2012-02-09
Bump** still not heard from anyone, was in another thread but it got solved for differnt reasons than my own.
I have bio's etc. just need a solution for fixing ingame memory cards. someone mentioned about installing Hardinfo? i downloaded it but i dont know how to install it. :/

---

### Post by MrBandicootKid on 2012-02-09
You need a bios for it to read the memory card.

---

### Post by kriltos on 2012-02-10
aww really? i thought a bios was for playing the game. : /


Ok. new question. How to i create a folder for such files to live in?

  hypothetically if i wanted to use the mentioned files the path would need to be in

/usr/pcsx/bios or another folder but both are not per missioned correctly. 

Is there a Terminal command i can use to input files?

---

### Post by rajke88 on 2012-07-16
> **MrBandicootKid said:**
> You need a bios for it to read the memory card.

Mark this topic as solved. MrBandicootKid solved it with text i quoted above. Default bios emulator in pcsx doesn't allow you to manipulate memory cards. But when i replaced it with original bios file, everything worked perfectly. Here are the steps for the beginners. 

1) copy your bios file to ```
/home/yourusername/.pcsx/bios
```(note .pcsx is hidden folder press ctrl + h to see hidden folders in nautilus)

2) open pcsx and go to menu Configuration> Plugins & Bios
[IMG]http://img254.imageshack.us/img254/3951/screenshotfrom201207161s.png[/IMG]

3) Select pasted bios here
[IMG]http://img152.imageshack.us/img152/7532/screenshotfrom201207161.png[/IMG]

Thats all, hope i helped. Have fun!

---

