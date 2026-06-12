---
title: "strange switch off Hoary/Cedega/HomeWorld"
date: 2005-06-22
forum: Gaming &amp; Leisure
---

### Post by edemark on 2005-06-22
Hi everyone

I have experienced a really stange thing when i was playing homeworld in my ubuntu hoary box with cedega. What has happened that after finishing a mission in the game my computer just SWITCHED OFF itself. I thought that it was some power failure (though i am working on a compaq nx9010 laptop but anyway) However today when i got some free time i played this game again. And Again it has SWITCHED OFF the machine. It did not just stopped working but did switch the coputer down. So I became a bit worried abaut if it was normal. Just because i see linux non as a "pls switch me off" machine but rather one that is all right being left swithed on 

Please help me to find out what causes this problem

pd i used to play this game without problems with suse 9.1

thanks

---

### Post by WMCoolmon on 2005-06-29
Check out this site: [http://www.thereisnospork.com/projects/homeworld/](http://www.thereisnospork.com/projects/homeworld/)

---

### Post by edemark on 2005-06-30
[QUOTE=WMCoolmon]Check out this site: [http://www.thereisnospork.com/projects/homeworld/](http://www.thereisnospork.com/projects/homeworld/)[/QUOTE]
 Thanks for the note I have came across that site but as i am having cedega why not to use it. Anyway I have resolved this problem. It was because my X is set up 32 bit while the game was running 16 or 24 something like that and that was causing the problem. So since i have changed to 32 bits it works all right.

Thanks again

---

### Post by edemark on 2005-07-07
[QUOTE=edemark]Thanks for the note I have came across that site but as i am having cedega why not to use it. Anyway I have resolved this problem. It was because my X is set up 32 bit while the game was running 16 or 24 something like that and that was causing the problem. So since i have changed to 32 bits it works all right.

Thanks again[/QUOTE]
 So my earlyer idea was not the one or only one that helped me play the game. I had installed lm-sensors before i changed color depth. So i was thinking that it really was this color depth issue but a cuple of days ago i uninstalled lm-sensors and for my bigest surprice homeworld started to swith of the computer again. So i reinstalled lm-sensors and xsensors just to be sure and the game is ok again.
Can it be some heat issue regulated by lm-sensors?
Any idea?

---

### Post by RJARRRPCGP on 2005-07-14
Because the PC is shutting down, probably a processor overheating problem.

Some motherboards have anti-processor overheat protection. The anti-overheat protection is supposed to shut down the motherboard if the processor temperature threshold is exceeded.

This problem is common with people that build thier own PC, because of the heatsink not being seated properly and thus when gaming, the processor starts overheating.

---

