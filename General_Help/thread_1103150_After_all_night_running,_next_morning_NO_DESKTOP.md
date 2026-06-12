---
title: "After all night running, next morning NO DESKTOP???"
date: 2009-03-22
forum: General Help
---

### Post by miguel64086 on 2009-03-22
Hello all,
I have a puzzling issue.
I usually keep my ubuntu 8.10 always running... but lately when I came up in the mornings, there is no desktop. I mean, no icons, no bar on top, etc. I just shows my wallpaper.
I can move the mouse, but no keyboard either. I mean, the num-lock light is lit, but when I hit it, the light does not even answer... So I got power to my USB keyboard, but it's not reponding either (so I can't go to the shell either)
Please help, I don't even know where to start, what log to look for, etc.
What changed?  I remember downloading some upgrades, but I couldn't tell you which ones.

Thanks

---

### Post by NT4usB on 2009-03-22
Sounds like it's locked up. Overheating? You take the side off and blow out the dust recently?
Do any keys work? Can you Ctrl+Alt+F1 to a tty and restart gdm?

---

### Post by miguel64086 on 2009-03-22
Thank you for your reply NT4usB.
No, I don't think it's overheating, since the fan is still going and I haven't notice abnormally hot computer.
The keyboard just doesn't response. I can't even get Ctrl+Alt+F1 to try to get to the cmd line.
Thanks

---

### Post by NT4usB on 2009-03-23
Do you have another computer on your network, or you could plug into the network and ssh into the locked one?

---

### Post by miguel64086 on 2009-03-23
You know... I knew I was going to be asked that.
I haven't try it yet... 
I guess it has been faster to just reboot that PC than to boot up my  XP machine... but next time it happens, I would do. (probably this PM)

---

### Post by stalkingwolf on 2009-03-23
you might try rebooting into the recovery mode, then run fix broken packages.

---

### Post by NT4usB on 2009-03-23
> **miguel64086 said:**
> You know... I knew I was going to be asked that.
I haven't try it yet... 
I guess it has been faster to just reboot that PC than to boot up my  XP machine... but next time it happens, I would do. (probably this PM)

The object would be to look around (lm-sensors?) and read the logs, see what may be malfunctioning. Info that may not be available after a hard boot.

---

### Post by NT4usB on 2009-03-23
> **stalkingwolf said:**
> you might try rebooting into the recovery mode, then run fix broken packages.

I'm leaning toward hardware. Power supply, dirty fans, heat sinks, etc.
I had a Netgear gigabit switch go bad once. Hard locked my MythTV box nearly every day. Get home from work and find it hung. 
Finally caught it in the act one weekend, lights on the switch started twitching. Otherwise I'd have still been chasing it.

---

### Post by miguel64086 on 2009-03-23
Thank you NT4usB
It could be hardware, since this is a 2 y/o PC.
I am able to SSH into my PC, but no idea what to look for.  Did you say lm-sensors?  where are those?  I did a find and no results.

I boot up in recovery mode now and fix one broken packages, and updated 6 packages.
After loading, I got a message that said that volume controls failed to load. I reload them and everything looks fine now, however, I will not know till tomorrow.

Thanks

---

### Post by NT4usB on 2009-03-24
Two is not old. As long as you've blown the dust out of the CPU heatsink, memory, cards, etc. lately.
I have a couple 10 year old boxes that run fine.

Did you look at the dmesg and other log  files while you were in there?

lm-sensors is in the repositories. Install and configure it. It displays some temps of MB, CPU, etc.```
sudo sensors-config
``` iirc, to configure. Y to everything. modprobe or reboot to load the modules.

run```
sensors
```from a terminal to see the temps.

Ususlly the numbers are random and meaningless since they need some correction in the config file before they show the actual correct temps.
I use them as a reference. Look at the temps in the BIOS at boot time. Then look at what sensors say soon as it boots. This gives a rough idea of where the numbers should be.
Any time you have a terminal open you can check temps.
There is a GUI, xsensors, in the repos that you can run on your desktop (when it's working *g*)

---

### Post by miguel64086 on 2009-03-24
OK...
Tonight same issue, so I configure the lm-sensors.
Not easy task, but google is my friend.
This is the output

```
w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.26 V  (min =  +0.00 V, max =  +1.74 V)
in1:        +12.20 V  (min =  +5.97 V, max = +13.41 V)
AVCC:        +3.34 V  (min =  +0.99 V, max =  +0.00 V)   ALARM
3VCC:        +3.34 V  (min =  +0.56 V, max =  +0.22 V)   ALARM
in4:         +0.05 V  (min =  +0.84 V, max =  +1.70 V)   ALARM
in5:         +1.59 V  (min =  +0.44 V, max =  +0.42 V)   ALARM
in6:         +5.25 V  (min =  +0.95 V, max =  +2.05 V)   ALARM
VSB:         +3.34 V  (min =  +2.82 V, max =  +1.60 V)   ALARM
VBAT:        +3.26 V  (min =  +1.57 V, max =  +3.23 V)   ALARM
Case Fan:      0 RPM  (min =   75 RPM, div = 128)  ALARM
CPU Fan:    2636 RPM  (min = 2033 RPM, div = 4)
Aux Fan:       0 RPM  (min = 2909 RPM, div = 16)  ALARM
fan4:          0 RPM  (min = 18750 RPM, div = 8)  ALARM
fan5:          0 RPM  (min = 11250 RPM, div = 8)  ALARM
Sys Temp:    +39.0Â°C  (high = -63.0Â°C, hyst = +100.0Â°C)  sensor = thermistor
CPU Temp:    +50.5Â°C  (high = +80.0Â°C, hyst = +75.0Â°C)  sensor = diode
AUX Temp:     +4.5Â°C  (high = +80.0Â°C, hyst = +75.0Â°C)  sensor = thermistor
cpu0_vid:   +1.350 V

```

Then I rebooted and re-run it again, the only big difference was on the CPU Temp, that dropped to 37ºC

I'll shut down the PC tonight,run it again tomorrow morning, and then tomorrow night and compare values.

Thanks

---

### Post by NT4usB on 2009-03-25
lm-sensors is one of the less friendly packages to install but hey, that's how we learn *g*.
50.5 on the CPU is a little high but not out of line. How does that compare to what the BIOS shows when you boot? 
For instance, the BIOS on one of my boxes shows 27°C but sensors shows 37°C soon as I boot. 
When I look at sensors and see 37C, I know (I think?) it's actually 27C. Plenty cool.

All this is fun but it's not going to isolate the lockup problem.
Time to grab some logs next time you ssh into the locked up box.
```
cat /var/log/Xorg.0.log >/home/*yourusername*/xorglog
and
dmesg >/home/*usernsme*/dmesglog
cat /proc/meminfo >/home/blabla/meminfolog
```
will dump those into your home folder. Reboot and post them up.

While you have the side off, blowing all the dust out of the fans, heatsinks, etc. pop the cards, ram, etc., and re seat them. Sometimes a loose card...
Also, might run memtest from the boot options for a couple hours. Could be a stick has gone bad.

At this point I'm just looking and guessing since many things can cause the lock up.
I'm no expert. 
I chase the things I know to look at and hopefully trip over the answer.

---

### Post by miguel64086 on 2009-04-01
OK.  Update time.
I think this issue started when I changed my screensaver from "AntSpotlight" to "Molecule" because my wife thinks little ants crawling on my screen was creepy.
Well... Last Monday I got bored with the nerdy "Molecule" and now I'm just using "Blank Screen" and it stopped happening.  Go figure./


I guess I didn't get to troubleshoot the actual issue, but I did learn about the LM-Sensors.

CPU Temp: +40.5ºC.... 10 degrees lower than before!

Thanks for all your help.

---

### Post by the_ice.e on 2009-04-02
> **NT4usB said:**
> 
For instance, the BIOS on one of my boxes shows 27°C but sensors shows 37°C soon as I boot. 
When I look at sensors and see 37C, I know (I think?) it's actually 27C. Plenty cool.


The bios dosnt use the procesor at high "speeds" thats whi the temp is cooler.. but when the loading starts the procesor can heat up (+ 10-20C°) in a second..

cudnt help ma self :D

---

### Post by xenophed on 2009-04-02
check your Xorg.0.log file you will see an error it would probable help if you could do a remote login or try.that would help narrow the problem down as I belive it is a X issue.I think this a MAJOR PROBLEM and should be move to the bug squad for tracking and fix as it is more common than thought

---

### Post by NT4usB on 2009-04-02
> **the_ice.e said:**
> The bios dosnt use the procesor at high "speeds" thats whi the temp is cooler.. but when the loading starts the procesor can heat up (+ 10-20C°) in a second..

cudnt help ma self :D

Well, how about that...
I had a 3.0 Cedar Mill chip in my Mbe/fe showed 10°C in the BIOS and 35°C after boot. 
Ambient was ~20°C.
Freakin' Ubuntu is a resource hog.

---

### Post by miguel64086 on 2009-04-03
> **xenophed said:**
> check your Xorg.0.log file you will see an error it would probable help if you could do a remote login or try.
I got the Xorg.0.log file but I don't see any errors.
Now, I don't know if that log would keep a history, since I haven't had a problem since I change screen savers...  but the bottom line is that those log files don't show any obvious errors.

---

