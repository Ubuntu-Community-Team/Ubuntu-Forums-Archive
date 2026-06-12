---
title: "Wine + CS1.6 System Freeze"
date: 2007-06-01
forum: Gaming &amp; Leisure
---

### Post by Alex Fernandez on 2007-06-01
I've got the game working, more or less. I mean I can get ingame, I can play - a bit - with decent performance (70fps and decent sound) - however I am having a few issues that I cant work out "why".

Firstly, downloading any ingame content (be it map, sound or sprays) almost instantly crashes my whole system (I have to do a power off/on reboot) - I can live with this, because I can disable the downloads via cl_allowdownload and cl_download_ingame - however if anyone has any clues how to fix this the suggestions would be most welcome

This second issue is the real problem, after about 10 min of playing (no matter what map/server) once again the whole system freezes forcing me to do a power off/on reboot. Now, my line of thinking has been that this is either a driver (fglrx) issue or a wine resource use issue (ie it runs out of RAM/swap), but I've had no luck in tracing this any further, so again any suggestions welcome.

For the record I'm running latest Wine (from WineHQ site) and latest ATI drivers (from ATI site), but even trying older wine + fglrx has had no effect (ie the ones from the Ubuntu apt repos. do exactly the same thing).

[Edit - almost latest wine I have .37 but .38 came out today]

---

### Post by CM Xtasy on 2007-06-02
> **Alex Fernandez said:**
> I've got the game working, more or less. I mean I can get ingame, I can play - a bit - with decent performance (70fps and decent sound) - however I am having a few issues that I cant work out "why".

Firstly, downloading any ingame content (be it map, sound or sprays) almost instantly crashes my whole system (I have to do a power off/on reboot) - I can live with this, because I can disable the downloads via cl_allowdownload and cl_download_ingame - however if anyone has any clues how to fix this the suggestions would be most welcome

This second issue is the real problem, after about 10 min of playing (no matter what map/server) once again the whole system freezes forcing me to do a power off/on reboot. Now, my line of thinking has been that this is either a driver (fglrx) issue or a wine resource use issue (ie it runs out of RAM/swap), but I've had no luck in tracing this any further, so again any suggestions welcome.

For the record I'm running latest Wine (from WineHQ site) and latest ATI drivers (from ATI site), but even trying older wine + fglrx has had no effect (ie the ones from the Ubuntu apt repos. do exactly the same thing).

[Edit - almost latest wine I have .37 but .38 came out today]

I have the exact same freeze issue and nobody has helped me with it.  I hope someone can find an answer :(

---

### Post by YokoZar on 2007-06-03
Updating Wine *won't* help - it's not a Wine problem.  From the Wine FAQ: [http://wiki.winehq.org/FAQ#head-9d93db2588a3de850b0d42b1944431ac24534caa](http://wiki.winehq.org/FAQ#head-9d93db2588a3de850b0d42b1944431ac24534caa)

> If you are getting a complete deadlock and are unable to even use your mouse after running Wine, it's probably not a specific problem with the Wine software. Wine is a user-level process, and shouldn't be able to completely hang the operating system under any circumstances. Instead, Wine is likely exposing a deeper problem with the system, such as a defective hardware driver.

---

### Post by Alex Fernandez on 2007-06-03
I can move my mouse, its just that the game (from within wine) is using 100% cpu/ram (I can hear the fan go mad) - and I think it may well be a wine based issue do to the error that I get when the system crashes: 

err:ntdll:RtlpWaitForCriticalSection section 0x7e4e3640 "x11drv_main.c:
X11DRV_CritSection" wait timed out in thread 0017, blocked by 0009, retrying (60
sec)

Now, I'm no expert on how Wine works, but from my understanding that is an error between Wine and X - which results in a 60 second delay in the action, which causes the system freeze. (I've seen this error with a few other apps, but most just hang without crashing the system - so it cant be a driver only issue. The driver may well be the reason for this error between Wine and X, but it is Wine that actually crashes the system in the end).

Even if the actual game crash is not fixable, it is certainly fixable to prevent wine from killing the whole system if that was changed to instead kill the app instead of letting it go on and crash the system.

---

