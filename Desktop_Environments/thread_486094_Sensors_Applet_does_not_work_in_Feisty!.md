---
title: "Sensors Applet does not work in Feisty!"
date: 2007-06-27
forum: Desktop Environments
---

### Post by PryGuy on 2007-06-27
Hello everybody!

I installed 'sensors-applet' in Feisty but it says that there is 'No sensors enabled!'... :(
I also installed 'lm-sensors', 'xsensors', 'collectd-sensors', 'hddtemp' and 'collectd-hddtemp' but there's still no luck...

Sensor 'hddtemp' appears in Sensors Applet Preferences but I can't enable it.

I read that 'lm-sensors' uses 'i2c' kernel module but it says 'FATAL: Module i2c not found.' when I modprobe it though it is said in the manual that the 'i2c' module is 'distributed directly with the kernel'. 

I feel a bit confused here... Any suggestions?

---

### Post by sharke on 2007-06-27
In a terminal sensors-detect answer yes to all questions . This will inatall the moduke for you.
Regards
Sharke

---

### Post by PryGuy on 2007-06-28
Thanks a lot! 
Some of my sensors do not display temperatures correctly though :(

---

### Post by madzieph on 2007-06-29
How do I configure sensor-applet to retain the configuration that I set? Each time I reboot the machine, the settings go back to the default values...

thanks

---

### Post by kvonb on 2007-07-09
Bump!

Same thing here, the settings are not retained!

There seems to be rather a lot of unanswered threads these days, and a lot of little problems in Feisty :S.

---

### Post by kvonb on 2007-07-11
All of a sudden mine saved the settings!!!!

I have no idea why, nothing changed.

I booted this morning and the settings I made last night stayed!

Must be those damned aliens again :S

---

### Post by orb9220 on 2007-07-11
> All of a sudden mine saved the settings!!!!
I have no idea why, nothing changed.
I booted this morning and the settings I made last night stayed!
Must be those damned aliens again :S

Nope I drove to Redmond and snatched a Virgin Microsoft Employee and sacrificed him to "The Fires of Goddess Ubuntu" and all is well again.

---

### Post by kvonb on 2007-07-11
> **orb9220 said:**
> Nope I drove to Redmond and snatched a Virgin Microsoft Employee and sacrificed him to "The Fires of Goddess Ubuntu" and all is well again.

...well, I would have tried that, but Redmond is rather a LONG drive from here ;)

---

### Post by langnix on 2007-09-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/sensors-applet/+bug/94558](https://bugs.launchpad.net/ubuntu/+source/sensors-applet/+bug/94558) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				regarding the problem of loosing the settings .. 
(I just removed the hdtemp package as a quick fix .. and it works for me)

---

