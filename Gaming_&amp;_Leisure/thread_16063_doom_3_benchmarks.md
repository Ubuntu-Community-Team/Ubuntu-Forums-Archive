---
title: "doom 3 benchmarks"
date: 2005-02-18
forum: Gaming &amp; Leisure
---

### Post by morphodone on 2005-02-18
Hey guys,
I did some doom 3 benchmarks comparing nvidia drivers and kernel optimizations.

here's the [link](http://home.comcast.net/~morphodone/space-monkeys/linux_tips.html#nvidia) 

let me know what you think

---

### Post by leech on 2005-02-20
Nice benches.  I've ran mine at 1280x1024 with Ultra High settings and it was about 70fps.  Though I still haven't figured out how to get AA on, when I set it, and it asks to restart the game to take effect, then I go back into the screen for it, and it says it's off again.

Also, I was wondering if you know if it's better to have Fast Writes enabled in Linux, as opposed to Windows.  A lot of people in the nvidia forums have issues in Windows and stuttering if they enable Fast Writes.  I was wondering if anyone knew if that was the case in Linux..  Guess I could try it, if I wasn't too lazy to re-install Doom 3 again....

Leech

---

### Post by ember on 2005-02-20
Thanks for your benchmark. It confirmed my suspection that it's not necessary to spent to much time in optimizing kernels. 

Would be interesting to see how a corresponding ATI card performs (I would offer to do some tests, yet my card (as seen in different entries here) doesn't work and I'm going to get a Nvidia card too)). Maybe there's someone who likes to test.

---

### Post by morphodone on 2005-02-20
[QUOTE=leech]Nice benches.  I've ran mine at 1280x1024 with Ultra High settings and it was about 70fps.  Though I still haven't figured out how to get AA on, when I set it, and it asks to restart the game to take effect, then I go back into the screen for it, and it says it's off again.

Leech[/QUOTE]

man, you must have one heck of a machine to get those numbers  :grin: 
i enabled AA and it stayed on...do you have the latest doom patch?
also, you might be able to enable it with the nvidia settings utility
personally i don't ever turn it on, i just try to run every game at really high resolutions...

[QUOTE=leech]
Also, I was wondering if you know if it's better to have Fast Writes enabled in Linux, as opposed to Windows.  A lot of people in the nvidia forums have issues in Windows and stuttering if they enable Fast Writes.  I was wondering if anyone knew if that was the case in Linux..  Guess I could try it, if I wasn't too lazy to re-install Doom 3 again....

Leech[/QUOTE]

I did a little googling and read that even if you enable fast writes it may not produce that much of a real world difference anyhow.  But if you get bored, enable it and let us know what you think.

---

### Post by morphodone on 2005-02-20
[QUOTE=ember]Thanks for your benchmark. It confirmed my suspection that it's not necessary to spent to much time in optimizing kernels. 

Would be interesting to see how a corresponding ATI card performs (I would offer to do some tests, yet my card (as seen in different entries here) doesn't work and I'm going to get a Nvidia card too)). Maybe there's someone who likes to test.[/QUOTE]


i used to have a 9700 pro but i gave it away b/c i struggled many a time to get
their drivers to work.  i was able to do so only once or twice out of countless tries
on various distros.  i like to support nvidia b/c they have decent linux drivers that are at least installable by most people.

---

### Post by valadil on 2005-02-20
Just out of curiosity what did you do differently in the custom 2.6.10 kernel?  Well besides ridding yourself of modules that your box doesn't need.

---

### Post by leech on 2005-02-20
> man, you must have one heck of a machine to get those numbers
i enabled AA and it stayed on...do you have the latest doom patch?
also, you might be able to enable it with the nvidia settings utility
personally i don't ever turn it on, i just try to run every game at really high resolutions... 

Actually it's not too much beefier than yours.  I have an AMD Althon64 3200+ (90nm) with 1gb of Corsair memory (running dual-channel at 400mhz) and an eVGA 6800GT.  Nothing is overclocked.  I'll have to re-install doom 3 as soon as I get my new hard drives that I just ordered (2 200gb Seagate SATA drives).  My old 36gb Ultra160 SCSI drive just isn't big enough anymore and to buy SCSI drives that are that big  would make me broke for the next decade....

I think a lot of the speed differences that I have with your system could be due to the RAM.  Seems to me that with the newer game engines (FarCry, Half-Life 2, Doom 3) that RAM makes a HUGE difference on performance.  I know it did with FarCry.  I could hardly even play it when I had my P4 3.06ghz and 512MB of RAM.  Not that it wasn't playable... but it would have to cache a lot of things after first loading before it wouldn't be choppy.  For example, when you first fired a gun after loading up the game, it would have to pause in the middle of the firefight to load sounds into memory.

Leech

---

### Post by morphodone on 2005-02-20
[QUOTE=valadil]Just out of curiosity what did you do differently in the custom 2.6.10 kernel?  Well besides ridding yourself of modules that your box doesn't need.[/QUOTE]

that's about it, however i did toggle k8 support (opteron, athlon 64) instead
of 386 support for processor...didn't seem to make a lot of difference
for all the trouble
i think the k7 kernel works just as well

---

### Post by YokoZar on 2005-02-21
Thank you, that was rather useful.

---

### Post by david.ballester on 2005-03-25
FYI:

Try to 'tune' nvidia and doom3 engine. Normally, as other people says in different benchmarks, tuning video/game makes values higher on Linux than Windows

HTH

[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=54](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=54) 

[http://www.doom3linux.com/](http://www.doom3linux.com/)

---

