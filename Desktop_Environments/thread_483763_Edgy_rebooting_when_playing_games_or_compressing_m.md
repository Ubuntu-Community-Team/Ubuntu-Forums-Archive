---
title: "Edgy rebooting when playing games or compressing mp3"
date: 2007-06-25
forum: Desktop Environments
---

### Post by OoooMatron on 2007-06-25
Does anyone know where i can start to try and find out my problem with my PC spontaneously rebooting?

It only seems to happen when the PC is doing something intensive. If i convert wav files to mp3 for example, it usually resets the PC at some point.

Yesterday I installed Second life on the machine and within 5 minutes of playing (every single time) the PC rebooted.

I am pretty sure it's not the games fault because I have been experiencing these reboots before.

---

### Post by Jonne on 2007-06-25
Try testing your memory (memtest86 is on the ubuntu liveCD). Running the memory test takes a few hours, but make sure you run it completely.

Also, check if you're running the right kernel for your processor.

---

### Post by OoooMatron on 2007-06-26
Ran the ram tester overnight for 8 hours. Not a single error reported.

uname -r reports
2.6.20-16-generic

I have p4 3ghz (hyperthreading). No idea if the HT is supported by the kernel.

Any logs i can look through? Nothing much in the syslog.

---

### Post by Jonne on 2007-06-26
it could be a pure hardware thing too:
-your power supply is underpowered, making your computer reboot when it's drawing too much power (and a P4  is kinda power hungry. Add a heavy gfx card and a few hard drives to that...).
-it just gets too hot inside the case, and the computer shuts down because of that. Try one of the temperature monitor applets to keep an eye on that while encoding your wavs.

Do you get the same in other OS'es, or is Ubuntu the only one on your box?

---

### Post by OoooMatron on 2007-06-26
i got pclinuxos and windows.

Windows seems ok while mp3 encoding and playing games.

Pclinuxos i need to test.

i do draw a lot of power though, i have 4 hard discs and an nvidia pciex card. 5900fx i think.

---

### Post by Jonne on 2007-06-26
Hmm, normally Ubuntu shouldn't be using more resources than Windows. If windows is fine, I guess it's an Ubuntu issue then.

I can't think of anything else, but may i ask why you're still on Edgy?

---

### Post by OoooMatron on 2007-06-29
whoops, I mean Fesity! I'm using 7.04.

 Ubuntu Stduio has the same problem.

---

### Post by OoooMatron on 2007-07-07
I installed Granular (pclinuxos based) and the computer doesn't reboot when performing the tasks mentioned above.

I do get system log messages saying the temperature is over threshold though.

---

### Post by OoooMatron on 2007-07-17
ok i cleaned out my heatsink and fans and Ubuntu lasts a lot longer but it still reset itself. The cpu temperature accroding to the bios was 65.

Is there some kernel setting or ubuntu setting that triggers a reboot? It seems like some kind of threshold setting.

---

### Post by OoooMatron on 2007-07-20
seems to be my 350w PSU is not up to the job of running 4 hard discs, dvd writer, gfx card etc :D

---

