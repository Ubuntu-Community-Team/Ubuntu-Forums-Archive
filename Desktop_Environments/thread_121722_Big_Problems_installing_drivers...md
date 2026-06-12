---
title: "Big Problems installing drivers.."
date: 2006-01-25
forum: Desktop Environments
---

### Post by Rock Lobstah on 2006-01-25
I'm brand new to Ubuntu, as reliable windows decided to crap out on me, and the only windows CD I have is just a repair disk! So, I'm currently using 64-Bit Ubuntu.

I did this..
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

since the guide instructed you to do that before you add any nVidia drivers.

Then I entered this..
[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

And I got a bunch of errors. I'm pretty sure it was something to do with the extra repositories, but I can't remember exactly what they were. Any, it suggested I manually update to try and fix it. 

"sudo apt-get update
sudo apt-get upgrade"

Alright, well that didn't work immedietly, but I tried both things and then the update again, and it asked me to put in my Ubuntu CD (not that I know why), and then it finished. It said to reboot.. and when I did, everything was messed up. I was in a text only mode, basically just looking at a huge terminal window. I'm afraid to try it again :(

PS: I realize that's an older version of Ubuntu, which could have caused the problem, but I couldn't find a good guide for 5.10.

---

### Post by astoltz on 2006-01-25
That guide should work EXCEPT that all references to "hoary" (5.04) should be replaced by "breezy" (5.10).  You may have already caught that but if not, make the switch and then do ```
sudo apt-get update
```Now having said that, I don't think that's the problem.  Note which version of the kernel you're using:```
uname -r
``` Then be sure you have the corresponding "linux-restricted-modules package installed.```
sudo apt-get install linux-restricted-modules-[kernel-version]
```The kernel version is the output from the uname -r command.  Now cross your fingers and try re-booting

---

### Post by Iandefor on 2006-01-25
Just to make certain: you are aware that, for basic desktop usage, the VESA driver works like a charm for NVIDIA cards?

---

### Post by Rock Lobstah on 2006-01-26
[QUOTE=Iandefor]Just to make certain: you are aware that, for basic desktop usage, the VESA driver works like a charm for NVIDIA cards?[/QUOTE]

Oh really? I was really on interested in the drivers because System --> Preferences --> Screen Resolution won't let me raise my res over 1024 x 768, and won't allow my refresh rate over 60Hz (which is damn annoying), even though I know my monitor can do 12x10 @ 100Hz and 16x12 @ 75Hz..

What are the "VESA" drivers, and would they solve my res / refresh rate problem? (would the nVidia drivers even help?)

---

