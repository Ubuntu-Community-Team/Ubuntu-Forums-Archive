---
title: "Steam Crashes at Updating User Configuration"
date: 2018-02-14
forum: Gaming &amp; Leisure
---

### Post by Turkten on 2018-02-14
Hello, 

     I'm relatively new to ubuntu. I've used it in the past but still pretty new with it overall. I've searched all over and can't find someone with the same issue I'm seeing with Steam so I thought I'd ask for help here. The error log is referencing line 927 of steam.sh. I've included the error log below as well as attached a screenshot of the portion of steam.sh in question (let me know if more is needed). I appreciate any help or direction at all! I'm at a loss and have no idea what else to try. 

```
rm: cannot remove '/home/rae/.steam/steam': Is a directory
rm: cannot remove '/home/rae/.steam/bin': Is a directory
Installing breakpad exception handler for appid(steam)/version(1513371133)
Installing breakpad exception handler for appid(steam)/version(1513371133)
Installing breakpad exception handler for appid(steam)/version(1513371133)
Installing breakpad exception handler for appid(steam)/version(1513371133)
Installing breakpad exception handler for appid(steam)/version(1513371133)
Installing breakpad exception handler for appid(steam)/version(1513371133)
Installing breakpad exception handler for appid(steam)/version(1513371133)
Installing breakpad exception handler for appid(steam)/version(1513371133)
Installing breakpad exception handler for appid(steam)/version(1513371133)
Installing breakpad exception handler for appid(steam)/version(1513371133)
Installing breakpad exception handler for appid(steam)/version(1513371133)
Installing breakpad exception handler for appid(steam)/version(1513371133)
Installing breakpad exception handler for appid(steam)/version(1513371133)
Installing breakpad exception handler for appid(steam)/version(1513371133)
Installing breakpad exception handler for appid(steam)/version(1513371133)
/home/rae/.steam/ubuntu12_32/../ubuntu12_64/gldriverquery: 1: /home/rae/.steam/ubuntu12_32/../ubuntu12_64/gldriverquery: Syntax error: "(" unexpected
Installing breakpad exception handler for appid(steam)/version(1513371133)
Generating new string page texture 2: 48x256, total string texture memory is 49.15 KB
Generating new string page texture 3: 384x256, total string texture memory is 442.37 KB
Installing breakpad exception handler for appid(steam)/version(1513371133)
Installing breakpad exception handler for appid(steam)/version(1513371133)
Installing breakpad exception handler for appid(steam)/version(1513371133)
Illegal instruction (core dumped)
Installing breakpad exception handler for appid(steam)/version(1513371133)
/home/rae/.steam/ubuntu12_32/../ubuntu12_64/vulkandriverquery: 1: /home/rae/.steam/ubuntu12_32/../ubuntu12_64/vulkandriverquery: cannot create ÀÐ@¤/@8: Directory nonexistent
/home/rae/.steam/ubuntu12_32/../ubuntu12_64/vulkandriverquery: 1: /home/rae/.steam/ubuntu12_32/../ubuntu12_64/vulkandriverquery: ELF: not found
/home/rae/.steam/ubuntu12_32/../ubuntu12_64/vulkandriverquery: 1: /home/rae/.steam/ubuntu12_32/../ubuntu12_64/vulkandriverquery: Syntax error: Unterminated quoted string
Installing breakpad exception handler for appid(steam)/version(1513371133)
Installing breakpad exception handler for appid(steam)/version(1513371133)
Installing breakpad exception handler for appid(steam)/version(1513371133)
Installing breakpad exception handler for appid(steam)/version(1513371133)
Generating new string page texture 4: 256x256, total string texture memory is 704.51 KB
roaming config store loaded successfully - 36112 bytes.
migrating temporary roaming config store
Failed to init SteamVR because it isn't installed
crash_20180214180618_1.dmp[18895]: Uploading dump (out-of-process)
/tmp/dumps/crash_20180214180618_1.dmp
/home/rae/.steam/steam.sh: line 927: 18847 Illegal instruction     (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"
crash_20180214180618_1.dmp[18895]: Finished uploading minidump (out-of-process): success = yes
crash_20180214180618_1.dmp[18895]: response: CrashID=bp-15d196dc-bdbd-4db4-9571-f3fcb2180214
crash_20180214180618_1.dmp[18895]: file ''/tmp/dumps/crash_20180214180618_1.dmp'', upload yes: ''CrashID=bp-15d196dc-bdbd-4db4-9571-f3fcb2180214''

```

---

### Post by oldrocker99 on 2018-02-15
You **did** install Steam from the Ubuntu repos? I hope so.

---

### Post by Turkten on 2018-02-15
Yes, after I updated everything with apt, I installed steam from the repos. I'm actually just messing with it because I found an old laptop in the closet and decided to mess around with it. I've actually had multiple versions of ubuntu on it with the same result each time. Maybe the hardware is just too old to support it properly. I didn't think that would be the case but I suppose it could be. 

I've tried some of the fixes for other, similar issues I've found digging through forums but I haven't found any topics anywhere that had the exact issue I'm having.

---

### Post by again? on 2018-02-15
Have you ever had steam running.
What gfx are you using?
```
lspci -k | grep -A3 VGA
```

---

### Post by Turkten on 2018-02-18
It's an old Intel chipset. 915GM. I used intel's update tool. Everything works fine as far as OGL support. I can play Warcraft III with wine and ePSXe works fine. I'm not expecting miracles but I do have several linux-native games in my steam library that aren't too demanding so I thought I'd try them out. I mainly want it just so I can message friends on steam. 

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Dell Mobile 915GM/GMS/910GML Express Graphics Controller
	Kernel driver in use: i915
	Kernel modules: i915, intelfb

```

---

