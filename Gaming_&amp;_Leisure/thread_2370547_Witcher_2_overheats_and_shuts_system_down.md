---
title: "Witcher 2 overheats and shuts system down"
date: 2017-09-04
forum: Gaming &amp; Leisure
---

### Post by Hasimir on 2017-09-04
First time playing the game I went for almost 5 hours with no incident.
The next day after a little more than 3 hours the computer instantly shut down.
The next day this happened after a bit more than 2 hours.
Today it died after about 30 minutes.

Everything else works fine, but when I fire up this game (using nVidia drivers at LOW game graphical settings) the computer overheats (or at least that is my assumption) and shuts down.
What can I do?
The pc is just a few months old, can it already be needing internal cleaning so bad that it overheats this much?
No other activity causes this problems.

Help?

- I was looking for a way to manually set the fan speed to maximum at all times while I play, I failed to find anything.

---

### Post by Doug S on 2017-09-04
Are you running thermald?
Perhaps use turbostat (part of the linux-tools-common package) to monitor temperatures while you do your game. I'm not sure which version you will end up with, and the syntax keeps changing, but anyway this is what I would suggest:
```
$ [COLOR="#FF0000"]sudo turbostat --quiet --hide SMI,C1,C1E,C3,C6,GFX%rc6,GFXMHz --interval 2 --Summary[/COLOR]
Avg_MHz Busy%   Bzy_MHz TSC_MHz IRQ     C1%     C1E%    C3%     C6%     CPU%c1  CPU%c3  CPU%c6  CPU%c7  CoreTmp PkgTmp  Pkg%pc2 Pkg%pc3 Pkg%pc6 PkgWatt CorWatt GFXWatt
1       0.04    1602    3411    196     0.00    0.00    0.00    99.97   0.14    0.00    99.82   0.00    35      37      0.13    0.00    99.41   3.95    0.21    0.23
1       0.03    1599    3411    182     0.00    0.00    0.00    99.97   0.12    0.00    99.85   0.00    35      36      0.12    0.00    99.45   3.94    0.20    0.23
203     6.13    3302    3411    465     0.00    0.00    0.00    93.86   6.24    0.00    87.63   0.00    48      48      0.13    0.00    50.58   11.12   7.37    0.23
301     9.11    3287    3411    581     0.00    4.78    0.00    86.10   18.75   0.00    72.13   0.00    48      48      0.09    0.00    16.60   15.58   11.82   0.23
300     9.04    3312    3411    570     0.00    0.00    0.00    90.95   9.14    0.00    81.82   0.00    49      49      0.12    0.00    27.26   14.59   10.84   0.23
300     9.04    3312    3411    579     0.00    0.00    0.00    90.95   9.14    0.00    81.82   0.00    48      48      0.12    0.00    27.25   14.60   10.85   0.23
^C

```Where you see that once I applied a bit of load to my system, the package temp went up about 11 degrees.

---

### Post by Hasimir on 2017-09-05
Yes, I have thermald 1.5.4 installed and running.

I've tried running the command you suggest
```
[COLOR=#FF0000][FONT=&quot]sudo turbostat --quiet --hide SMI,C1,C1E,C3,C6,GFX%rc6,GFXMHz --interval 2 --Summary[/FONT][/COLOR]
```
but it fails as there is no turbostat for my kernel (currently 4.13.0)
the linux prompt says I should install:
linux-tools-4.13.0-041300-genericlinux-cloud-tools-4.13.0-041300-generic

I tried but they don't exist
I tried with the generic version, and they installed fine, but still turbostat is not working and producing the same error as before

---

### Post by mastablasta on 2017-09-05
try psensor: [https://wpitchoune.net/psensor/](https://wpitchoune.net/psensor/)

also he wrote to use [COLOR=#000000] linux-tools-common package.

> [/COLOR][COLOR=#000000]The pc is just a few months old, can it already be needing internal cleaning so bad that it overheats this much?[/COLOR][COLOR=#000000]

yes it can. it can build up incredibly fast. and at this point you do not know if CPU is overheating or maybe the GPU. dust is especailly problematic on laptops. 

on the old desktop i have i am puling in cold air and pushing out the warm one. th eflow is a lot bigger than on laptops, but still dust build up quite fast. i can only imagine what is in my lungs. ugh. i live quite close to the road and can't wait for the promissed and long overdue bypass onth eother side of town.

[/COLOR]

---

### Post by Hasimir on 2017-09-05
I have installed both psensor and freon (a gnome extention) to monitor my temperatures.
I'll now try to run the game in Window Mode, so that I can concurrently keep an eye on the temperature panels.
So far my normal use temperature (like, right now) seems to be around 44 °C
Playing the Witcher it seemed to go as high as 80-90 °C ... as a constant temperature.
But I'll have more details after today's tests.

---

### Post by mastablasta on 2017-09-05
you are very close to "T Junction" which is 100C according to this site : [https://ark.intel.com/products/95451/Intel-Core-i7-7500U-Processor-4M-Cache-up-to-3_50-GHz-](https://ark.intel.com/products/95451/Intel-Core-i7-7500U-Processor-4M-Cache-up-to-3_50-GHz-)
assuming you are playing on the ZenBook in your signature. working temps should be arround 80C or a bti over (somepeople report throttling at 90 others at 100C. Shutdows are usually after that.

compressed air will clean it, or you can get an external heater once you confirmed it is the heating that is causing it.

problem with laptops CPU is you can't easilly reapply the thermal paste. it could be that it wasn't applied well. who would know?!

---

### Post by Hasimir on 2017-09-05
Yes, the rig in my signature is the one I use and the one I'm talking about in this thread :)

One thing that puzzles and worries me is the fact that the time-to-shutdown has been rapidly decreasing. I fear damage to the hardware might occur (or has already happened?). Is this a sensible worry, or am I just overreacting?
Also... the current solution appears to be to open and clean the machine. Or bring it to a technician to do the same and maybe check the thermal paste? (I'm terrified about causing damage myself, this is my main and only computer, and I need it for... everything >__<)

---

### Post by mastablasta on 2017-09-05
well if more dust is gettign build up then the time will be getting shorter and it will overheat faster. you can buy a can of compressed ait (they are relatively cheap) and then just spray it in the vents in short bursts. hopefulyl that will help. 

if it's only a few months old and still under warranty you could get this done by after sales service for free. they usually have air compressors for that and shouldn't take them long to do it (a minute or so).

regarding the paste - some of these laptops nowadays have CPU soldered on the motherboard. i wouldn't do it myself. especially if it is still under warranty.

---

### Post by Hasimir on 2017-09-05
Net info gathered using Freon while playing in window mode.
The sensor lists the following temperatures:

GeForce 940MX
C0
C1
Package ID 0
Temp1
Temp1
Temp1

At the time of shutdown, after about 20 minutes of play, the situation was as follows:
GeForce 940MX - around 78°c
C0 - around 94°c
C1 - around 87°c
Package ID 0 - around 88°c
Temp1 - around 78°c
Temp1 - around 82°c
Temp1 - around 42°c

I'm not sure what the various things are.
I guess the video card and the 2 cores of the cpu. Not sure about the rest?

---

### Post by Doug S on 2017-09-05
If ti were me, I would change /etc/thermald/thermal-conf.xml to this:
```
<?xml version="1.0"?>

<!--
use "man thermal-conf.xml" for details
-->

<!-- BEGIN -->
<ThermalConfiguration>
        <Platform>
                <Name>Overide CPU default passive</Name>
                <ProductName>*</ProductName>
                <Preference>QUIET</Preference>
                <ThermalZones>
                        <ThermalZone>
                                <Type>cpu</Type>
                                <TripPoints>
                                        <TripPoint>
                                                <Temperature>55000</Temperature>
                                                <type>passive</type>
                                        </TripPoint>
                                </TripPoints>
                        </ThermalZone>
                </ThermalZones>
        </Platform>
</ThermalConfiguration>
<!-- END -->

```But note that I have set a ridiculously low trip point temperature of 55 degrees. Test it first, then maybe raise it to 75 degrees.
Save a copy of the original xml file first.

---

### Post by Hasimir on 2017-09-05
This would activate the fans whenever the temperature raises above 55°c ... right?

---

### Post by Doug S on 2017-09-05
> **Hasimir said:**
> This would activate the fans whenever the temperature raises above 55°c ... right?No, It would throttle back the maximum CPU clock frequencies, thereby reducing the amount of heat generated.

---

### Post by mastablasta on 2017-09-06
your heat is quite high. are the fans working at full speped on shutdown? if so it may be that you just have a buildup of dust (would be easy to solve).

the only other issue i can think of for new PC regarding high heat is drivers - nvidia has a PPA where newer versions can be obtained. you porbably need bumblebee installed as well to do the switch form intel to nvidia, but i guess you already know that. if ther eis some firmware drivers fo rintel in additional drivers mkae sure you install those as well.

regarding fanspeed control:
how to contorl fan speed
[https://askubuntu.com/questions/22108/how-to-control-fan-speed](https://askubuntu.com/questions/22108/how-to-control-fan-speed)
Arch documentation on fanspeed control (note that Arch has very good documentation. it can't always be applied to Ubuntu, but sometimes it explains how things work really well. and apps are the same).
[https://wiki.archlinux.org/index.php/Fan_speed_control](https://wiki.archlinux.org/index.php/Fan_speed_control)

---

### Post by Hasimir on 2017-09-06
PANIC!

I tried following the instructions in the Fan Speed link.
I got stuck as step 3 ... running **sudo pwmconfig **tells me that [COLOR=#111111][FONT=Ubuntu]"There are no pwm-capable sensor modules installed".
In the same thread they suggest a fix for this, which is [/FONT][/COLOR]setting [B]acpi_enforce_resources=lax
[/B]to do this I followed instructions that made me edit GRUB turning "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" into "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
then I run **sudo update-grub** and restarted the system

This broke my system for some reason :(
My trackpad doesn't work anymore.
My configured command Super+PowerButton doesn't summon the shutdown options (suspend / restart / powerOff) but instead shuts the computer down directly.
The volume keys (Fn+F10 F11 F12) don't work anymore.
Freon can't detect anymore the temperature of the nVidia card or the second Core (but maybe that's because I switched to the Nouveau drivers in the meantime?)
On startup the overall system feels weird... slower... it actually hangs for a few moments right after I log into my account... a thing it was not doing before.

And, in all of this, the **sudo pwmconfig **command still yields no results :P

What can I do? ¢_¢

---

### Post by Hasimir on 2017-09-06
UPDATE!

Crisis averted.
I booted with an older kernel, then used Ukuu to remove and reinstall the latest one.
Apparently disabling the ACPI stuff edited something in the kernel that lingered even after ACPI were enabled again.

Now everything works fine again.
Of course, still no fan control... but I'm starting to think that it is not an available option at all, for hardware reasons :/

---

### Post by Doug S on 2017-09-06
> **Hasimir said:**
> Of course, still no fan control... but I'm starting to think that it is not an available option at all, for hardware reasons :/Are you saying that your fan does not go faster at all as a function of temperature?

I do not normally run thermald, because I don't have to, but I installed it and am using the .xml file I listed previously, but with a trip point of 73. If I load down my system the fans go much faster as the processor package temperature eventually hovers around 73 degrees.

The reason I thought your troubles might be processor temp rather than graphic temp is that you listed your processor core 0 temperature as the higher limit (94 degrees) in a previous post.

---

### Post by mastablasta on 2017-09-07
you can edit the grub line only temporary at boot. no need to edit the grub file, then have a panic attack.

read here: [https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter](https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter)

---

