---
title: "Battery always shows 0%"
date: 2009-01-09
forum: General Help
---

### Post by Charbs on 2009-01-09
Ive looked around at some of the threads about this same subject but the info in them seems to be a bit outdated. Im wondering if anyone knows a fix for this.

Im running Ubuntu 8.10 and the battery indicator on my laptop always reads 0% no matter what. Weather im charging or discharging, the pop up says:

"Computer is running on battery power
Laptop battery discharging (0.0%)
Battery discharge time is currently unknown"

When plugged in it says pretty much the same thing but charging:

"Computer is running on AC power
Laptop battery charging (0.0%)
Battery charge time is currently unknown"

My battery is fine because I can run off the battery for a good 2 hours so that shouldnt be the problem. If anyone has any information on why this is happening or how to fix it, it would help me greatly. 

Mainly because when im running on battery there is no warning when the computer is about to die, and it will jsut abruptly shut off with no warning. Simply cuz Ubuntu doesnt know how much time is remaining and when to warn me.

---

### Post by Charbs on 2009-01-10
Some more info if this helps anyone:

/proc/acpi/battery/BAT1/info

present:                 yes
design capacity:         6000 mAh
last full capacity:      unknown
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 250 mAh
design capacity low:     150 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            JM-6
serial number:           3761513358
battery type:            LION
OEM info:                Hewlett-Packard

/proc/acpi/battery/BAT1/state

present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      unknown
present voltage:         unknown


This has to do with some sort of ACPI problem, but ive tried ACIP=FORCE but doesnt help.


More info when I run sudo acpi -V in terminal before and after I unplug the power cable.

WITH AC ADAPTER:

charbs@charbs-laptop:~$ sudo acpi -V
[sudo] password for charbs: 
     Battery 0: Full, 100%
  AC Adapter 0: on-line
     Thermal 0: ok, 53.0 degrees C
     Cooling 0: Processor 0 of 10

WITHOUT AC ADAPTER (Just after unplugging)

charbs@charbs-laptop:~$ sudo acpi -V
     Battery 0: Discharging, 100%, 71582:46:00 remaining <---------(This will stay at 100% forever even when batter is low)
  AC Adapter 0: off-line
     Thermal 0: ok, 54.0 degrees C
     Cooling 0: Processor 0 of 10
charbs@charbs-laptop:~$ 


So as you can see, my battery is somewhat recognized, but the Power Management icon wont register any info properly.

---

### Post by Charbs on 2009-01-15
Cmon guys, dont leave me hangin. There must be someone out there who knows how to fix this.

---

### Post by dr3amx on 2009-01-16
I have this exact problem. I have Ubuntu 7.04. My laptop was working on battery till it was discharged and turned off automatically. When I plugged AC on, it's not showing battery state.
I tried installing Linux Mint 6 and nothing changed. I even tried removing the battery and other tricks from some forums but no luck.
Any help is very appreciated.
Regards

---

### Post by Charbs on 2009-01-26
Just on a side note. I tried updating my BIOS and it didn't help.

This is really annoying. Not knowing when my battery is about to die or how long til it is fully charged is NOT COOL!!!!!

---

### Post by dr3amx on 2009-01-29
Anyone?! Some support please :(

---

### Post by Charbs on 2009-03-04
Just wanted to let people know that I STILL havent found a fix for this problem yet. Is there anyone out there that can help at all?

---

### Post by huzefa_from_kuwait on 2009-05-18
Exact Same  battery, exact same problem, exact same output. Any help would be highly appreciated.
Thanks.

---

### Post by huzefa_from_kuwait on 2009-05-24
Hey mine suddenly started to work, i was just playing around with acpi related files and I rebooted and bang ! the battery started to suddenly show off with beautiful green colour filling with 99.2 % and charging. also there are a lot of different colours dots appearing now in power history !. the problem is i dont remember what I did that it started to work, coz i restarted 3 hours after i screwed it.

---

### Post by Charbs on 2009-05-24
Thats great news, and also the worst news I could have heard, not knowing how you fixed it. :)

Oh Well, atleast we now know its fixable. Do you have the same laptop/battery? Compaq Presario v2000 series?

---

### Post by huzefa_from_kuwait on 2009-05-25
try Installing hdparm and check out its options... i think hdparm -W 0

---

### Post by Charbs on 2009-05-31
Hmm. that didnt seem to help. What exactly am i supposed to do with that?

Im very jelous that you have a working battery and i dont :)

---

### Post by Charbs on 2009-07-05
Im still stuck on this 0% battery situation, if there's anyone out there that can help, i would really appreciate it.

Thanks.

---

### Post by p0cky84 on 2009-07-05
> **Charbs said:**
> Im still stuck on this 0% battery situation, if there's anyone out there that can help, i would really appreciate it.

Thanks.
Can you please discribe the problem more detailed?

Is this on the retail software?  The gnome panel? In which case what applet is it? etc.

---

### Post by Charbs on 2009-07-05
Ive put tons of details in the first two posts of this thread. Im not sure what else I could put. The only difference is that im now using Ubuntu 9.04 64bit. But the problem still exists.

---

### Post by villalcalde84 on 2009-07-05
Hi everyone!

I have the exact same problem, and I am using Ubuntu 8.04. Please, if anyone knows how to fix this, please share the answer because this problem is very annoying.

I've had this issue for several months I think, and it is terrible not knowing how much time the battery has before it dies.

I attach an image showing the problem.

Thanks!

---

### Post by Charbs on 2009-07-06
Cmon people, can we please get some help with this or is it just a pipe dream to fix a 0% battery on Ubuntu, or any distro for that matter, i get the same result on Kubuntu, OpenSUSE, Mandriva, and Fedora. 

Nothing will recognize my battery properly. Except ofcourse, Windows :P

---

### Post by Charbs on 2009-07-07
I found this on another thread, havent tried it yet tho



"I had the same issue with Hardy (going from the stock 3 cells to a 6 cells).

You'll have to remove the Gnome Power Manager battery profile files to ensure
proper calibration with new battery.

Code:
ps -e | grep gnome-power-man


Read the process ID : example, 6807 ? 00:00:00 gnome-power-man, 6807 here.

Code:
sudo kill -9 XXX
(replace XXX with process ID, 6807 in previous example)

Code:
rm ~/.gnome2/gnome-power-manager/*.csv


There are two csv files for each battery (related to detected battery ID) : one for
charging, one for discharging.

Then reboot, and do a full battery cycle (charging / discharging) to calibrate the
profile. Avoid going under 5-10%, modern Li-Ion batteries need a minimal charge for
the included electronic regulation system."

---

### Post by Charbs on 2009-08-08
I dont really feel comfortable trying out that last technique, so im STILL sitting here with no battery info. In case anyone cares :)

---

### Post by Charbs on 2009-09-02
ok well i tried that theory in the previous post, and it didnt help. Battery is still not showing up. This is a lost cause.

---

### Post by jjgomera on 2009-09-02
I had a similar problem the battery of a asus in 8.04, 8.10 and 9.04, i had to install kernel 2.6.30 from backports to solve

---

### Post by Charbs on 2009-09-02
im running 2.6.28-15-generic right now, how would i go about gettin that kernel that your using?

EDIT: Ok i was able to install 2.6.30, didnt change a thing, battery still constanly 0% no matter what

---

### Post by poppo_g on 2009-09-05
I have almost the same problem. My Gnome panel batterymeter says that it can't say ho much power the battery has left and how much time before the battery is full.

ls /proc/acpi/battery says BAT1
cat /proc/acpi/battery/BAT1/info says present: no.

However I can work for about 2,5 hours on my battery before the laptop shuts down without a warning :-(

Please help!

---

### Post by misfitpierce on 2009-09-05
Also just a note... everyone with batteries should atleast charge then discharge laptop completely monthly... If you leave plugged in all the time you ruin the battery over time and my friends did same thing in windows and ubuntu because battery cells got ruined from always being plugged in.

---

### Post by huzefa_from_kuwait on 2009-09-15
what does cat /proc/acpi/battery/BAT0/state  say?

The remaining capacity can show approximately how much battery is still left.

---

### Post by Charbs on 2009-09-15
That file is empty

---

### Post by kehon on 2009-11-01
I have this problem on my compaq presario c700 and it occurs after the computer goes to sleep or hibernates and when it comes back up. Has anyone found a solution yet?

---

### Post by JBAlaska on 2009-11-01
You might try [lm-sensors](http://www.lm-sensors.org/). Install it from the repo, then run the sensor detect script;
```
sudo sensors-detect
```, then if it detects your sensors, you can use a app like gkrellm to display the output graphically. 

Note: There is a updated detect script on the linked site that detects more sensors.

Good Luck

Edit: OOPS, Necro thread LOL

---

### Post by ikacer on 2009-11-01
> **JBAlaska said:**
> You might try [lm-sensors](http://www.lm-sensors.org/). Install it from the repo, then run the sensor detect script;
```
sudo sensors-detect
```, then if it detects your sensors, you can use a app like gkrellm to display the output graphically. 

Note: There is a updated detect script on the linked site that detects more sensors.

Good Luck

Edit: OOPS, Necro thread LOL

I don't think lm-sensors can detect the battery state anyway. that is usually done with /proc/acpi/battery/BAT0/info which in this case is reporting 
remaining capacity: unknown

---

### Post by JBAlaska on 2009-11-01
I thought that also..but it does probe alot of modules..Thought it might be worth a shot. Even if it doesn't work..they might like gkrellm LOL

---

### Post by pjalegria on 2009-11-01
My problem is a little different, when i unplugged from AC it still showing the icon from "AC plugged", so i dont now is capicity...

---

### Post by kehon on 2009-11-01
none of that works. I think it might be a problem with the suspend and waking up for laptops because it only happens when the laptop comes back from suspend.

---

### Post by Parikx on 2009-12-11
I am using Dell 1550 and I am also facing the same problem

Every time i see the battery icon on my taskbar it says "Laptop Battery is fully Charged" and it just gets turn off without giving any warning. I have tried many solutions but still I am facing the same problem.

---

### Post by cevocruz on 2009-12-12
It worked! When I commanded `cat /proc/acpi/battery/BAT0/state` it started work immediately, but in my case the battery was BAT1 instead BAT0. Maybe this was the problem. I really don't know wich was the effect of the command in the configuration path of the battery on linux. I will try to test this on my other 2 notebooks (another Karmic, and one old LinuxMint Gloria) that seems to have the same problem. It worked on my Acer AO751H running Karmic.

---

### Post by drpponnu on 2010-05-14
:mad:> **Charbs said:**
> Ive looked around at some of the threads about this same subject but the info in them seems to be a bit outdated. Im wondering if anyone knows a fix for this.
 
Im running Ubuntu 8.10 and the battery indicator on my laptop always reads 0% no matter what. Weather im charging or discharging, the pop up says:
 
"Computer is running on battery power
Laptop battery discharging (0.0%)
Battery discharge time is currently unknown"
 
When plugged in it says pretty much the same thing but charging:
 
"Computer is running on AC power
Laptop battery charging (0.0%)
Battery charge time is currently unknown"
 
My battery is fine because I can run off the battery for a good 2 hours so that shouldnt be the problem. If anyone has any information on why this is happening or how to fix it, it would help me greatly. 
 
Mainly because when im running on battery there is no warning when the computer is about to die, and it will jsut abruptly shut off with no warning. Simply cuz Ubuntu doesnt know how much time is remaining and when to warn me.

---

### Post by dou on 2010-05-14
You didn't use the batteries in a right method.To buy a new one 
[www.digital-camera-batteries.net]("http://www.digital-camera-batteries.net")

---

### Post by WarrenSH on 2010-05-14
Dell Inspiron 2200

I am running 9.10 LTS 32bit & my battery shows 27% all the time plugged in or unplugged :(

---

### Post by isbiyanto on 2010-05-18
> **dr3amx said:**
> I have this exact problem. I have Ubuntu 7.04. My laptop was working on battery till it was discharged and turned off automatically. When I plugged AC on, it's not showing battery state.
I tried installing Linux Mint 6 and nothing changed. I even tried removing the battery and other tricks from some forums but no luck.
Any help is very appreciated.
Regards

I have same problem on lenovo 3000 G410 :confused:

---

### Post by oxf on 2010-06-26
> **isbiyanto said:**
> I have same problem on lenovo 3000 G410 :confused:

This problem seems to have been around for a while. I just found this thread. I had it in Hardy, Karmic and now Lucid
I have  a Compaq Presario M2000 note book

---

### Post by oxf on 2010-06-27
This is depressing! A search of Launchpad reveals that this bug is being experienced all over. Whats strange is it was being reported several years ago and still persists in Lucid. Wonder why it's never been fixed?

---

### Post by domino1241 on 2011-06-12
I'm having a similar problem with a different cause.  My Asus 1005HA was near a window when it began to rain, and it was sitting in water when I found it.  I don't the computer itself got wet, because the 9-cell lifts it off the table top and the actual computer frame wasn't wet (just the rubber feet), but it was off with 0% battery, and I still get hours of work out of it!

Any new ideas on how to refresh the battery state?

---

