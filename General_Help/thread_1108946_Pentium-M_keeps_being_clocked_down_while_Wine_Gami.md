---
title: "Pentium-M keeps being clocked down while Wine Gaming, no matter what"
date: 2009-03-28
forum: General Help
---

### Post by juamez. on 2009-03-28
My problem consists of the following: when I play a game with wine (I never encountered another application that induces this behavior) the processor is ultimately clocked all the way down to the lowest possible clockspeed after a while.

First it seemed that the problem was temperature related, because it would occur far less to never when I clocked the cpu down myself one notch (from 1.87GHz to 1.6GHz) to not let it reach the suspected trigger temperature of something around 70°C. This worked for me while playing Carmageddon 2 and RollerCoaster Tycoon.

But I recently had the idea of playing Total Annihilation in Ubuntu, and since it worked I decided to play a few skirmish games. Although I did lower the clockspeed to 1.6GHz, the clockspeed quickly ramped down all the way to 800MHz. This cannot be caused by a too high temperature because of the lowered clockspeed. I also noticed that the ramping-down occured much faster and more aggressive when playing TA than playing any other game.

Since this slows my entire system down to a crawl, I decided to try doing something about it. Things I've done, to no avail:
- remove the powernowd package
- blacklist the acpi_cpufreq and all the governor modules
- put a modprobe -r acpi_cpufreq and for every other cpufreq module in the /etc/rc.local
- modprobe -r acpifreq and other cpufreq modules manually after system bootup

This all disables clockspeed control, aswell as removing monitoring options by removing the /sys/devices/system/cpu/cpu0/cpufreq directory.

Unfortunately, my cpu still clocks down, although I cannot see it directly since any clockspeed reporting tool is shut off, I notice it by feel and looking at the dropping temperature. Also, when I modprobe acpi_cpufreq again, I notice the current cpu clock is at 800MHz.

I am defeated and hopeless.

Is there ANY way to stop the system from clocking my processor down at its own will? I'm sick and tired of it, and I wished to be in complete control of my system, but seemingly that is not the case.

I do not have any option in my BIOS to either disable or enable Intel Centrino Speedstepping.

The computer in question is a Dell Latitude D610 laptop equipped with a Pentium M 1.87GHz.

edit: so far I found this thread about the same problem as mine: [http://ubuntuforums.org/showthread.php?t=1028201](http://ubuntuforums.org/showthread.php?t=1028201)

**UPDATE 1**
The cpu clockdown also occurs when a virtualbox VM (non-ose with windowsXP as guest os) is running and I have VLC playing a normal xvid file. Cpu temperature never exceeds 65°C. More details [here](http://ubuntuforums.org/showpost.php?p=6982210&postcount=4)

**UPDATE 2**
SOLVED! by disabling both BIOS speedstepping and removing the powernowd or cpufreqd package, whatever applies to your system configuration.

**FINAL UPDATE**
Really SOLVED now.

Necessary steps involved to stop the CPU from clocking down:
1) Disable Speedstepping in BIOS, but leave the powernowd package installed and working

Necessary steps involved to make Wine Gaming fluent:
1) the above
2) go to winecfg and set directsound to standard level and turn off emulation

---

### Post by 3Miro on 2009-03-28
I don't know how many people on this forum are using wine. It could be a wine issue, however, I have never experienced it. Did you look for such issues on the wine forums/bug DB. In general winehq is the better place for wine issues.

Have you checked the temperature when you are playing? What happens if you run a CPU extensive operation with out wine? Run some program (i.e. convert some video) and see if the CPU would clock down. That way you can know if it is Linux/ACPI/BIOS or just wine.

(note that most Linux processes do not take CPU power)

---

### Post by juamez. on 2009-03-28
I'm doing a conversion from xvid to x264 atm, and the cpu is mostly loaded by "nice" level load, at least that's what my system monitor applet is telling me.

The CPU temp is at 66°C and (possibly) still slowly rising, but that's not near the 70°C or more I got when using wine to play some games. I must say I got a lot of user level cpu load when using wine to play games, opposed to the nice level cpu load I'm getting while using Avidemux to convert a videostream. Does that make any difference in possible cpu frequency scaling?

The temperature is now fluctuating between 66°C and 67°C, still rising I guess, and I hope I will find out the answer soon.

Since Total Annihilation will cause the cpu to clock down even at temperatures below this one, I think it does not have anything to do with the temperature, but I don't know how I would explain the "solution" for the cpu clock-down phenomenon when playing Carmageddon 2 or Roller Coaster Tycoon if that's the case, since both SEEMED to respond positively to a lower cpu temperature.

I'm now another minutes further into the cpu stress test, and so far anything seems normal, no frequency scaling or anything. The temperature is now slowly getting to 68°C. Still no sign of any system response to the high temperature.

You might be right afterall, blaming this on Wine. Maybe I should try other versions of wine, or maybe Cedega (since they alter the wine package in some way, maybe they involuntarily fix this problem, who knows?) and look what that will bring me.

I'm now at a fixed 68°C and 10 minutes into the transcoding process. Still no sign of anything. If this completes without any frequency change, you convinced me. ;)

Thank you for pointing me to the right direction in this problem!

edit: the reason for the nice-level load is because avidemux is getting the transcoding done with nice set at 10. I'm getting temperatures of 68°C and 69°C at full stress. Still no lowered frequency, and 20 minutes into the process. Yay!

---

### Post by juamez. on 2009-03-30
It seems that I was cheering too early.

I'm now working with VirtualBox which puts a nice load on the cpu.

While it sits there idling about, I'm watching an episode of a series encoded in XviD with VLC, and guess what? There is the cpu again clocking down. Now I'm at 1.33GHz instead of the normal 1.87GHz. The governor is set to Performance. When I set it to userspace with a maximum clock of 1867000 (kHz) it just keeps sitting at a clock of 1.33GHz. Now that I've pauzed my episode in VLC to type this reply, the cpu just started climbing up to 1.6GHz and 1.87GHz where it started today. This does NOT occur when VirtualBox is running and VLC is paused.

I can confirm now that this is in no way Wine-related, since it is not running atm and has not run since the laptop booted.

I can also confirm that in my quite extensive reach of experiences with gaming on this laptop while in Windows, I did not notice any moment where the cpu clocked down for any reason, even if the temperature did go over 70°C.

To be quite frankly: what is going on here? I dislike it when I don't know the cause of such behavior.

---

### Post by kevmitch on 2009-03-30
If it is throttling, it sounds like its the bios that's doing it. Are there any bios settings for temperature throttling?

While 70 degrees doesn't sound like much to me, you might want to consider doing things to lower the temperature. If it's a laptop make sure it's on a flat, hard surface and nothing is obscuring the ventilation.

---

### Post by juamez. on 2009-03-30
I opened the laptop and replaced the thermal paste by Arctic Silver a couple of days ago, and I also cleaned the dust out of the heatsink.

The laptop is currently docked into a Dell docking station, where the processor is getting somewhat warmer than usual, but this problem occurs even at temperatures where the laptop is on a hard, flat and smooth surface.

If it's the BIOS, why wouldn't this occur when in Windows (XP)? Maybe I should do some more tests in Windows where the cpu is fully stressed, which is a situation that is far less frequent than in linux for some reason. Anyway, I'm pretty positive that I've played Civ2 in windowsXP, which keeps the cpu fully loaded all the time, but I also remember clocking down the cpu during the time I play the game because I like the cpu to produce less heat, and processor frequency isn't that much of an issue anyway in Windows for older games, since it does not have the defficiencies that Wine has while emulating a lot of windows-like behavior (but that might have something to do with the poorer 3D implementation of the Intel graphics driver in linux).

Anyway, I'm back to square one.

---

### Post by kevmitch on 2009-03-30
If you have removed all frequency setting modules and the frequency is still getting modified, it seems quite likely that it's being done by the BIOS because there's nothing else left to be doing it. Windows might have some way of communicating with the bios that is not available or might be set up differently in linux. Does your bios have any thermal settings that might pertain to this?

The reason that wine would be slower for games is that it has to translate directx graphics commands to opengl which is an additional step, so you should expect that to require more cpu power.

---

### Post by LowSky on 2009-03-30
You are confusing computer uses for speedstepping. The computer needs little processor watch a video, but to load a new application or to run a diagnositc it need more processing power. the lockdown is most likey from overheating, because if you are even close to 70'C then you are some issues. does the processor fan come on? Is it always on low and never going on high?

these things may effect the processor from using the correct stepping as the overheating is raising alarms with the BIOS


70'C is really hot. How do you even use the computer. It shouldn't get that hot. My desktop never goes over 45'C, and my Laptop never goes over 55'C.

I guess people don't realize that laptops are not meant for gaming or for heavy processor use.

---

### Post by change_mode on 2009-03-30
> **LowSky said:**
> 
70'C is really hot. How do you even use the computer. It shouldn't get that hot. My desktop never goes over 45'C, and my Laptop never goes over 55'C.

Pentium M CPUs can take up to 100°C so the temperature shouldn't be a problem.

---

### Post by LowSky on 2009-03-30
100'C is water boiling hot, just because the PC can handle it doens't mean the user can, or the computers other components.

---

### Post by change_mode on 2009-03-30
> **LowSky said:**
> 100'C is water boiling hot, just because the PC can handle it doens't mean the user can, or the computers other components.

Yea, but he's at 70°C, not 100.

---

### Post by juamez. on 2009-03-30
> **LowSky said:**
> You are confusing computer uses for speedstepping. The computer needs little processor watch a video, but to load a new application or to run a diagnositc it need more processing power.I'm well aware of that, but it even happens when I take (drastic) measures against speestepping that I mentioned above.> **LowSky said:**
> the lockdown is most likey from overheating, because if you are even close to 70'C then you are some issues. does the processor fan come on? Is it always on low and never going on high?
I'm using the i8k package to set the cpu-fan to maximum at a temperature of 55°C or higher, and to set it back to medium at 50°C or lower. Even without the i8k package the cpu-fan gets triggered and begins blazing at a temperature of somewhare above 50°C, so we can rule out the fan.

Also the cpu suffers from a CLOCKdown, not a lockdown. It means that the clockspeed (or clock frequency, whatever you'd like to call it) is lowered by means of lowering the multiplier, just the way speedstepping works.

Like I said: 70°C is the normal stress temperature for my laptop and does not do any weird things when I'm in windows.

> **LowSky said:**
> these things may effect the processor from using the correct stepping as the overheating is raising alarms with the BIOSPossibly, but how then do you explain the nonweird behavior in Windows? As far as I can tell everything is fine in windows.


> **LowSky said:**
> 70'C is really hot. How do you even use the computer. It shouldn't get that hot. My desktop never goes over 45'C, and my Laptop never goes over 55'C.

I guess people don't realize that laptops are not meant for gaming or for heavy processor use.The laptop gets that hot, it's designed to be portable and to withstand some heat. 70°C is within specs, though possibly just barely.

> **kevmitch said:**
> If you have removed all frequency setting modules and the frequency is still getting modified, it seems quite likely that it's being done by the BIOS because there's nothing else left to be doing it. Windows might have some way of communicating with the bios that is not available or might be set up differently in linux. Does your bios have any thermal settings that might pertain to this?Perhaps, but that would suck because there isn't much to do against bios-calls, or is there? My bios does not have any thermal settings available, no.

> **kevmitch said:**
> The reason that wine would be slower for games is that it has to translate directx graphics commands to opengl which is an additional step, so you should expect that to require more cpu power.Yes, that's logical. I must say I'm not sure if I suffer from significant performancelosses when playing 2D-games in Wine compared to windows. Maybe my computer is just overkill anyway for those games so that I won't notice any difference? But that's a minor inconvenience at most.

---

### Post by juamez. on 2009-04-01
I think I succeeded in keeping full control over the clock speeds, but I'm not 100% sure - as in: I need to do more tests before I'm completely sure.

Yesterday I went into the BIOS and I actually found a screen where I can disable speedstepping! What a surprise, I was thinking the whole time my laptop did not have any way to disable speedstepping in the bios, I was almost totally sure of it.

Anyway, I disabled the speedstepping in the bios and did some more tests. Now the weird part was that my cpu was slowing down in a way that was not related to frequency. That is my conclusion, because when I actually lowered the frequency of the cpu by means of the cpu frequency monitor applet, the temperature got even lower, so I assume it was something else. When looking into the throttling file, though, I only saw that the cpu was in the 100% state for the whole time, so that was not it.

I decided I'd try the cpufreqd with speedstepping-centrino module instead of powernowd, but it was the same story.

Today after some thinking: what if I disabled both BIOS speedstepping AND the powernowd package (by uninstalling it)? And what do you know? It (=the full experience) did not get slower at all while playing Total Annihilation. THAT is what I wanted.

Also since I still have acpi_cpufreq, I can still change my clockspeeds and use a performance or even ondemand governor, with the only downside of not being able to use the lowest possible frequency (800MHz), but 1,06GHz isn't that bad either.

So IF things tend to stay this way, I'd say this is solved.

edit: another tought: if cpu frequency control can be managed without BIOS speedstepping or the powernowd module, what in god's name do we need them for anyway?

---

### Post by juamez. on 2009-04-01
Only a part of the problem is solved now: I had to reinstall powernowd package again, because if I didn't, the clockspeed was fixed at 800MHz. The CpuFreqMon applet did not show anything because the acpi_cpufreq module failed to load, but I noticed by looking at the temperatures: 56°C instead of the normal 68°C. While TA remained playable, it is not really what I want since everything became a tad slower.

Now that I have reinstalled powernowd, I notice that TA does get slower while playing, but it seems that TA is the only thing left that is getting slower. So maybe that part of the problem is indeed Wine related, although I cannot find any clue to why that may be. I have played some Carmageddon 2 while a VirtualBox VM was running in the background producing a significant cpu load. All was well and stayed well, so I guess it's alright.

Now to find the solution for TA. Maybe when I reinstall my Ubuntu when 9.04 launches all my problems will be over. One can only hope, I guess.

---

### Post by juamez. on 2009-04-02
The problem apparently was that in WineCFG the directsound was set to "emulate" and to the "emulation" level instead of the standard level, with ALSA selected as soundcard source. Now I have unticked "emulate" and set level to "standard", and now everything works fine. Very fluent gameplay. I'm happy!

Conclusion: a Wine problem indeed.

---

