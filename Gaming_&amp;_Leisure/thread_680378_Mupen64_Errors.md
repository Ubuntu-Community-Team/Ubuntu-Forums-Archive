---
title: "Mupen64 Errors?"
date: 2008-01-27
forum: Gaming &amp; Leisure
---

### Post by OoteR on 2008-01-27
I used greenblobs tool to install on mythbuntu 7.10 64 bit and have had no luck running mupen from the command line. Here is the output: 
```
user@mythboxen:~/Desktop$ mupen64 
/usr/local/bin/mupen64: line 2: 12045 Segmentation fault      (core dumped) /usr/local/games/mupen64-0.5/mupen64
/usr/local/bin/mupen64: line 4: 12048 Segmentation fault      (core dumped) /usr/local/games/mupen64-0.5/mupen64
/usr/local/bin/mupen64: line 6: 12051 Segmentation fault      (core dumped) /usr/local/games/mupen64-0.5/mupen64
/usr/local/bin/mupen64: line 8: 12054 Segmentation fault      (core dumped) /usr/local/games/mupen64-0.5/mupen64
/usr/local/bin/mupen64: line 10: 12057 Segmentation fault      (core dumped) /usr/local/games/mupen64-0.5/mupen64
/usr/local/bin/mupen64: line 12: 12060 Segmentation fault      (core dumped) /usr/local/games/mupen64-0.5/mupen64
/usr/local/bin/mupen64: line 14: 12063 Segmentation fault      (core dumped) /usr/local/games/mupen64-0.5/mupen64
/usr/local/bin/mupen64: line 16: 12066 Segmentation fault      (core dumped) /usr/local/games/mupen64-0.5/mupen64
/usr/local/bin/mupen64: line 18: 12069 Segmentation fault      (core dumped) /usr/local/games/mupen64-0.5/mupen64
```

Anyone have any ideas or is it possible to get this running on 64 bit? 

Thanks,

~OoteR

---

### Post by aphirst on 2008-01-28
Quite frankly, I'm puzzled. It runs absolutely fine on my Ubuntu64.

Erm, there are only two times I got a segfault trying to run mupen64, so have a butcher's and they may give you a small hand:

1) mupen64 on 64bit doesn't like "Dynamic Recompiler", because the dynamic recompiler "dynamically recompiles" N64 code into raw 32-bit code (hence "Dynamic Recompiler" :P). Raw 32-bit code sems to epically fail on the 64-bit platform, so setting it up as "Interpreter" seems to do the job just fine. However, you seem to mention that you can't even run the program, so you may need to faff around with a configuration file (somewhere like /usr/local/games/mupen64/cfg ), and change the settings.

2) I have a USB gamepad. If you set up mupen64 to use your gamepad, and then you try to load the emulator with the gamepad unplugged, the emulator seems to go "Ack, where is the gamepad? AAAAARGH!!!" *fails*. Of course, again, you said that you couldn't get it to even run, so again, have a look in the configuration files.

Sorry I couldn't be of all that much help, but the whole point of Linux is problem solving (w00t: self satisfaction!).

Hope this can help. :lolflag:

---

### Post by Sockerdrickan on 2008-01-28
You can get more info about a new version being developed here [http://www.emutalk.net/forumdisplay.php?f=50](http://www.emutalk.net/forumdisplay.php?f=50) :)

---

### Post by frenchn00b on 2008-01-28
> **OoteR said:**
> I used greenblobs tool to install on mythbuntu 7.10 64 bit and have had no luck running mupen from the command line. Here is the output: 
```
user@mythboxen:~/Desktop$ mupen64 
/usr/local/bin/mupen64: line 2: 12045 Segmentation fault      (core dumped) /usr/local/games/mupen64-0.5/mupen64
/usr/local/bin/mupen64: line 4: 12048 Segmentation fault      (core dumped) /usr/local/games/mupen64-0.5/mupen64
/usr/local/bin/mupen64: line 6: 12051 Segmentation fault      (core dumped) /usr/local/games/mupen64-0.5/mupen64
/usr/local/bin/mupen64: line 8: 12054 Segmentation fault      (core dumped) /usr/local/games/mupen64-0.5/mupen64
/usr/local/bin/mupen64: line 10: 12057 Segmentation fault      (core dumped) /usr/local/games/mupen64-0.5/mupen64
/usr/local/bin/mupen64: line 12: 12060 Segmentation fault      (core dumped) /usr/local/games/mupen64-0.5/mupen64
/usr/local/bin/mupen64: line 14: 12063 Segmentation fault      (core dumped) /usr/local/games/mupen64-0.5/mupen64
/usr/local/bin/mupen64: line 16: 12066 Segmentation fault      (core dumped) /usr/local/games/mupen64-0.5/mupen64
/usr/local/bin/mupen64: line 18: 12069 Segmentation fault      (core dumped) /usr/local/games/mupen64-0.5/mupen64
```

Anyone have any ideas or is it possible to get this running on 64 bit? 

Thanks,

~OoteR

you may try to copy download the files into /home/myhomeuser/mupen64
and run it as $
no need to install normally

---

