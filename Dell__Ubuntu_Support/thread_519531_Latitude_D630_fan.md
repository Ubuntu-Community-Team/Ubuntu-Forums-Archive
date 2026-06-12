---
title: "Latitude D630 fan"
date: 2007-08-07
forum: Dell  Ubuntu Support
---

### Post by cklubi on 2007-08-07
hi,

so I got a brand new D630 and installed Feisty (currently 64bit version), as for others my dvdrw doesn't work (I know the solution and it works like that) and that WIFI is gone after suspending, but except that no big issues. But I have noticed that the fan seems to be running almost all the time, even when there's nothing "heavy" going on. Has anybody else noticed this, or it just me? I'm dual-booting with XP and there the fan is off most of the time. (or at least it runs so slowly with XP, that I can't hear/feel it running)

Even when I leave the computer idle, it takes A LONG time until the fan stops and after that for example launching "apt-get update" from terminal or just opening a folder window turns the fan on again.

(The same fan behaviour was also with the 32bit Feisty)

Can anybody with a D630 comment, if there's a similar fan behaviour for you too?

---

### Post by apel_2804 on 2007-08-07
I haven't seen this issue yet. Please post some environmental data like temperature, surface you use the notebook, etc.

---

### Post by cklubi on 2007-08-07
GNOME sensors applet only detects CPU sensor, this is around 34-38°C when computer is idle, during actual CPU usage it goes up to 46°C, but drops quickly back; hddtemp shows 40-41°C.  I couldn't get lm-sensors to work (should it even work with this chipset in D630?).

laptop's is on a usual office desk... room temp. might be 23-25°C during the day I guess, the desk is not in direct sunlight though.

EDIT: temperatures from running XP: CPU around 45°C (when not idle), disk temp is the same, 40-41°C.  So I'm just wondering why the fan seems to work more intensively when using Linux, compared to XP... :-k

---

### Post by lessthanjake on 2007-09-10
I have the exacly same problem with my d630 running Gutsy. It's extremely irritating. I actually bought this PC because of all the reviews telling how quiet it is. And running Windows is not an option at all!

I tried to use the i8kutils and it manages to turn my fan off, but then something else (BIOS / kernel / Gnome Power Manager / I don't know) is turning it right on again. This results in the fan oscilating on and off, making it even worse than when it was on all the time.

Anyone who knows a fix. Kernel patch, Unofficial BIOS or whatever :) Or just a simle elegant solution of cause.

---

### Post by HangLoose on 2007-09-10
I have an Inspiron and it really seems that the computer is struggling to make the temperature down in the system.

You should try to alter the cpu frequency, Ive set mine to 1Ghz but the odd thing is that every time that I restart the computer I need to RE set the thing.

Its not that much work, just adding some values depending on how many cores you have, but its still boring to do it.

At least my notebook now runs much cooler ;)

---

### Post by jonsson on 2007-10-18
I have a D630 with Kubuntu Feisty and my fans seem to run *a lot*

It's been mentioned here as well: [http://ubuntuforums.org/showthread.php?t=481651&page=11](http://ubuntuforums.org/showthread.php?t=481651&page=11)
but I haven't seen a solution yet. :confused:

---

### Post by mxt on 2007-10-19
Can the ones that are experiencing the fan issue post which graphic card they have ? 
It could be an issue related to nvidia cards..

---

### Post by janbala on 2007-10-21
Hi,

Same problem here on a D630/T7300/nividia quadro nvs running gutsy.

Using dellfand - [http://ubuntuforums.org/showthread.php?t=463590](http://ubuntuforums.org/showthread.php?t=463590) - doesn't solve the problem. The fan speed changes when the deamon polls temperature then goes back instantly to it's previous speed level.

---

### Post by jonsson on 2007-10-22
I don't have the Nvidia card but my fans still seem to run *a lot*. I have a standard D630 with Intel graphics.

I did some experimenting with i8fan the other day. I can monitor the fans and I can stop/slow them down but they instantly start again. :neutral:

---

### Post by trondhuso on 2007-10-23
The problem is also present on the D420. So it could be a Latitude DXXX problem.

-trond-

---

### Post by bwakkie on 2007-10-23
The fan problem is a hardware problem. A friend (a Network Administrator) of me had Dell replacing the motherboard for it, contact your dealer. Naturally the problem is the same on Windows.

---

### Post by sham_khot on 2007-10-27
Having same problem with my new latitude.
Fan are running constantly and making lot of noise.
Initially I thought it is fom Hard Drive.
Any one have any idea how to fix it?

---

### Post by cklubi on 2007-10-28
> **mxt said:**
> Can the ones that are experiencing the fan issue post which graphic card they have ? 
It could be an issue related to nvidia cards..

probably not only nvidia's problem, my D630 is with Intel's graphics.
does somebody have an idea, why it affects Ubuntu more than XP?

---

### Post by janbala on 2007-10-28
The temperature at which fans start to run is set by the BIOS. The level is set quite low for the D630 (around 40°C for low speed) 

I haven't found any software under Ubuntu able to supersedes BIOS settings and force  temperature threshold to a higher level (or lower). I don't have Windows so I can't say if Windows is able to do it but it wouldn't be surprising.

There has been this kind of issue on the Dx10 (and maybe Dx20) series and a BIOS update solved this issue.

---

### Post by dennissundman on 2008-03-04
Just wondering if there has been any progress in this topic. I have noticed that my d630 makes more sound in gnu/linux even when the cpu fan is not running - compared to windows. It seems to be yet another fan, that doesen't want to stop?

I flashed to the newest bios (A07) with the hope that this would solve the problem, but no...

---

### Post by Demonice on 2008-03-12
yes, i have the same problem too (on the d630). any solution yet?

---

### Post by ikivela on 2008-07-01
I got same problem too...

---

### Post by SnakePlisskenDD on 2008-07-07
I have nearly the same problem but the reason seems to be that my powermanagement especially the cpu frequency management is gone since an update some weeks ago. So the cpu is always running at maximum frequency. That would explain why the heavy fan usage.

I keep hoping for a patch to solve this problem.

---

