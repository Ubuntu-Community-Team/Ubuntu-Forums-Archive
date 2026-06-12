---
title: "CPU frequency stopped working after reboot"
date: 2008-12-11
forum: General Help
---

### Post by blakjesus on 2008-12-11
I followed the tutorial on [this thread]("http://ubuntuforums.org/showthread.php?t=248867") to change the frequency scaling of my computer and it successfully slightly increased my battery life and greatly decreased the temperature at idle.

After rebooting though, i can't get it to change my CPU frequency. I tried following the steps again and everything says its working but my CPU frequency doesn't change.

I did find something weird though, after typing the command 'cpufreq-info', the out put was this:

> cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  **hardware limits: 800 MHz - 2.53 GHz**
  **available frequency steps: 2.53 GHz, 2.53 GHz, 1.60 GHz, 800 MHz**
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: **frequency should be within 2.53 GHz and 2.53 GHz**.
                  The governor "conservative" may decide which speed to use
                  within this range.
  current CPU frequency is 2.53 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0 1
  **hardware limits: 800 MHz - 2.53 GHz**
  **available frequency steps: 2.53 GHz, 2.53 GHz, 1.60 GHz, 800 MHz**
  available cpufreq governors: userspace, powersave, ondemand, conservative, performance
  current policy: **frequency should be within 2.53 GHz and 2.53 GHz**.
                  The governor "conservative" may decide which speed to use
                  within this range.
  current CPU frequency is 2.53 GHz.

---

### Post by blakjesus on 2008-12-12
Bump. No one has any suggestions? :confused:

---

### Post by redilyn on 2008-12-12
Maybe try ondemand instead of conservative

---

### Post by blakjesus on 2008-12-12
Tried it already. No matter what setting it is on it says that the frequency that the scaler can choose must be between 2.53GHz and 2.53GHz

---

### Post by redilyn on 2008-12-12
I really don't know anything about cpu scaling and I don't have a mobile processor

but the thread says advanced options here -> cd /sys/devices/system/cpu/cpu0/cpufreq/ondemand

maybe there is something in that file that will help?

---

### Post by blakjesus on 2008-12-13
That only brings me to the directory, i dont know what to do from there. I tried opening the files in the folder with gedit but it wont open them.

---

### Post by redilyn on 2008-12-13
Maybe try adding the CPU Frequency Scaling Monitor to your panel, then try the steps listed below. Might be a helpful site too if you haven't read it already.

[http://hubpages.com/hub/Ubuntu--CPU-Scaling--Battery-life-and-You](http://hubpages.com/hub/Ubuntu--CPU-Scaling--Battery-life-and-You)

"how do you actively control this? It&#8217;s fairly easy. Right click on an empty space in your taskbar (where your applets and such things as Applications, Places and System are located) and choose &#8220;Add to panel&#8221;. From there, find the CPU Frequency Scaling Monitor. Double click on this and it will appear in your taskbar. Right click on it and choose Properties and you can set various options like have it show your CPU frequency as a frequency (i.e. 1.33Ghz) or as a percentage. If you have multiple CPU&#8217;s or a dual/quad core machine you can also choose which CPU to monitor.

To configure this applet to actually allow you to control how your CPU(s) scale, you&#8217;ll have to had back to the terminal.

Type this:

sudo dpkg-reconfigure gnome-applets

This will throw up a nifty blue screen asking you to say Yes. Do so. Then it will ask if you want to install cpufreq-selector with SUID root. Say yes. Once you&#8217;ve done this, go back to your CPU Frequency Scaling Monitor in your taskbar and left click it. You should now be presented with a bunch of options from which you can choose the one you want. You can also directly set the frequency at which your CPU(s) will run at, which can be handy if you want to scale up or down for a short bit and then manually change it again.."

Hope this helps

---

### Post by blakjesus on 2008-12-13
Yes, i'm aware of this applet. I already configured it to set my CPU frequencies and it was working untill i rebooted. Now If i try to change it, no matter what, it stays at 2.53GHz.

If you look at what my terminal displays after running cpufreq-info, it states

> ...
available frequency steps: 2.53 GHz, 2.53 GHz, 1.60 GHz, 800 MHz
...
  current policy: **frequency should be within 2.53 GHz and 2.53 GHz**.
                  The governor "conservative" may decide which speed to use

This is the same with ondemand, powersave, and conservative. From what i understand, it recognizes the available frequency steps, but something is telling it that all of ther different governors can only choose 2.53GHz.

What baffles me the most is how it was working until a reboot and doing the steps over again on the guide didn't work this time. There was no updating involved either, so it couldn't have been broken by updates.

---

### Post by redilyn on 2008-12-13
Like I said befor I have no way of testing any of this. Just throwing ideas your way.

such as editing /etc/default/cpufrequtils:

ENABLE="true"
GOVERNOR="ondemand"
MAX_SPEED=1391439
MIN_SPEED=662590

Have a look at those settings.

---

### Post by blakjesus on 2008-12-13
I don't even have /etc/default/cpufrequtils

I have /etc/default/cpufreqd but i have already poked around in there, and there's nothing helpful in there.

---

### Post by blakjesus on 2008-12-14
Bump.

Does no one else have any idea what's going on? :confused:

---

### Post by blakjesus on 2008-12-16
Bump.

---

### Post by blakjesus on 2008-12-17
Bump.

---

### Post by blakjesus on 2008-12-18
bump

---

### Post by redilyn on 2008-12-18
Doesn't seem like your getting much help....

"it will only be in effect until you reboot at which time your default settings will come back. To change the default head back into your terminal and type:

gconf-editor

From there head to apps -> gnome-power-manager -> cpufreq. Find the settings policy_ac and policy_battery and change them to whichever setting you want for the default."

---

### Post by blakjesus on 2008-12-18
I thank you because you seem to be the only one willing to bother to help me out.

But when i searched around for a fix, i cam across what you suggested. Unfortunately, i found out that during an Ubuntu system update they removed the cpufreq option from gconf-editor. I searched high and low but haven't found a way to reach this option.

If someone could just at least tell how to change this option outside of the gconf-edito so i can try it out at least would help...

---

### Post by redilyn on 2008-12-18
Just saw this. Any help??

sudo apt-get install cpufrequtils
sudo cpufreq-set -d <freq>

cpufrequtils 002: cpufreq-set (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
Usage: cpufreq-set [options]
Options:
-c CPU, --cpu CPU number of CPU where cpufreq settings shall be modified
-d FREQ, --min FREQ new minimum CPU frequency the governor may select
-u FREQ, --max FREQ new maximum CPU frequency the governor may select
-g GOV, --governor GOV new cpufreq governor
-f FREQ, --freq FREQ specific frequency to be set. Requires userspace
governor to be available and loaded
-h, --help Prints out this screen

---

### Post by blakjesus on 2008-12-18
Holy @#*$! :shock:

That actually worked! :mrgreen: My cpu is scaling as it did before i rebooted! I can't even begin to thank you enough! If you were here i would buy you a beer. :popcorn:

Thank you so much.

---

### Post by redilyn on 2008-12-18
Glad I could help :)

---

### Post by blakjesus on 2008-12-18
Hmm... I seem to be having another related issue. While this command fixes my problem, the scaler keeps reseting itself to 2.53GHz or 1.6GHz automatically every 10 minutes or so.

What causes this? the command provided is a temporary fix for it, but something keeps telling it to fix itself at 2.53GHz or 1.6GHz.

What is causing it to do this?

---

### Post by redilyn on 2008-12-18
Are you setting the freq for both cores?

sudo cpufreq-set -c 0 -d 800MHz -u 2.53 GHz -g ondemand
sudo cpufreq-set -c 1 -d 800MHz -u 2.53 GHz -g ondemand

Does it still reset back to a higher freq?

Are you sure there is no background programs that could be starting which are causing your proc to speed up?

Latest BIOS installed?

What happens when you try 

sudo cpufreq-set -c 0 -d 800MHz -u 2.53 GHz -g powersave
sudo cpufreq-set -c 1 -d 800MHz -u 2.53 GHz -g powersave

---

### Post by blakjesus on 2008-12-20
Yes i made sure that the frequency was set on both cores and i don't really know how to check if a process is causing a change in my scaler and yes i recently updates my BIOS.

When i run the command it works for about 30 minutes or until i leave my laptop and it goes into standby. After that it goes back to being stuck at 2.53GHz.

I found a workaround thanks to your help though, i setup a cron job to run the previously mentioned command every now and then. So far it is working ok besides the fact i have to use my cpu scaling monitor on my panel to switch from performance to ondemand every time i come back to my computer (before, i would have to do that and run the command)

EDIT: Actually when i changed my cron job to the command you just gave me it keeps my cpu scaling great. Every now and then i will see it get stuck again, but my cron job kicks in a few minutes later and fixes it.

So thanks alot. Without those commands, i would have been completely in the dark.

Although im not marking this as solved. There was no actual fix, just a workaround that i made up that hasn't been fully tested yet. So unless anyone can provide me with something to fix it with, im going to keep this open.

---

### Post by redilyn on 2008-12-20
Not sure if they are relevant.

You may need to set your BIOS to "maximum performance" if you are using Linux to set the CPU speed. This is necessary to prevent odd behaviour (cpufreq 'freezing' at certain frequencies)

---

### Post by blakjesus on 2008-12-20
There are other options in my BIOS about my CPU but none really for limiting the the CPU frequency or nanything like that.

---

### Post by redilyn on 2008-12-22
Another suggestion (Sorry for the delay)

Check the following file

```

sudo gedit /etc/cpufreqd.conf

```

Under the general section add

```

double_check=1

```

"Anyways, all of this can be corrected thanks to a very nice feature cpufreqd supports, which is namely

double_check=1

in the [general] section of /etc/cpufreqd.conf

this will make sure that the settings cpufreqd tries to put in place are correctly set by re-reading the scaling_max_freq and scaling_min_freq files, cpufreqd will then try to set it as long as it's not correct."

---

### Post by BDNiner on 2008-12-22
[http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867)

The first post details how to setup freq scaling. At the end you install the sysfsutils package which allows you to set the governor type at boot so you don't need a cron job to change the governor to powersave or ondemand and keep it there.

---

### Post by redilyn on 2008-12-22
While I hope that solves his problem, I believe if you read this thread you will find that was the tutorial he followed before all this happened :)

---

### Post by blakjesus on 2008-12-22
Yes, that is the guide i used. Everything was set up, and it didn't carry over after rebooting. Even after running through the process it didn't work because no matter which scaler i chose, something was telling it that it could _only_ use 2.53GHz. 

The command that redilyn provided fixed the frequencies that were available to the scalers, but something keeps locking the frequency at 2.53GHz (sometimes at 1.6GHz) usually after coming back from suspend or randomly after a few minutes. Since there appears to be no fix, i just found my own work-around by getting my computer to run the command that fixes the frequencies every few minutes (cron). After endless searching this seemed to be the only way to get scaling to work semi-properly.

---

### Post by kedmond on 2009-06-12
blakjesus, I'm so glad you posted this and kept bumping it.  I not only have the EXACT same problem as you, but the exact same processor and frequencies:

more /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
2535000 2534000 1600000 800000 

I guess I have no choice but to set up a crontrab like you, right?  *sigh*

-Kazem

---

### Post by unutbu on 2009-06-12
kedmond, please post the output of 
```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor            # shows the current governor
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors # shows available governors
```

---

### Post by kedmond on 2009-06-12
My available governors are:

conservative ondemand userspace powersave performance 

My current govenor is:

performance

I set it to ondemand with the Frequency Scaling Applet.  It will go to ondemand temporarily, for a few minutes, then switch back to performance.  What's amazing, though, is that when I run a CPU intensive task (such as rendering) it drops my CPU speed to 1.6 GHz or 800 MHz, and then it'll shoot it back up to 2.54 GHz when the machine should be idling.

I just kill cpufreqd now when I'm doing work and max out the CPU.

-kedmond

---

### Post by kedmond on 2009-06-12
Just for good measure, here is the output from cpufreq-info:


cpufrequtils 004: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]cpufreq@lists.linux.org.uk[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 2.54 GHz
  available frequency steps: 2.54 GHz, 2.53 GHz, 1.60 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
[B]  current policy: frequency should be within 1.60 GHz and 1.60 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.[/B]
  current CPU frequency is 1.60 GHz.
  cpufreq stats: 2.54 GHz:0.01%, 2.53 GHz:0.00%, 1.60 GHz:0.00%, 800 MHz:0.00%  (486)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 800 MHz - 2.54 GHz
  available frequency steps: 2.54 GHz, 2.53 GHz, 1.60 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
[B]  current policy: frequency should be within 1.60 GHz and 1.60 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.[/B]
  current CPU frequency is 1.60 GHz.
  cpufreq stats: 2.54 GHz:0.01%, 2.53 GHz:0.00%, 1.60 GHz:0.00%, 800 MHz:0.00%  (539)




This is immediately after telling the applet to switch to OnDemand.  It momentarily goes back to Performance, where it's at 100% (2.54 GHz) until of course you need some power, at which point it drops back to 800 MHz or 1.6 GHz...it chooses randomly.

-kedmond

---

### Post by unutbu on 2009-06-12
What happens when you run these commands:

```
echo ondemand | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand | sudo tee /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
```

Does the governor somehow revert to performance?

---

### Post by kedmond on 2009-06-12
When I first run those commands, the applet says I'm doing OnDemand, but both CPUs are at 100%.  Running top shows that nothing CPU intensive is actually running.  It's just stuck at 2.54 GHz arbitrarily.  This IS the real speed of the CPU, and not the applet lying.

It remained with OnDemand for ~2 minutes, and while I was doing some work, it went back to "performance" but pinned the CPU to 1.6 GHz while I was rendering an image (CPU intensive).  Once the render was complete, it was back to 2.54 GHz and still on "performance".  It's so weird.

Thanks for the response.

---

### Post by unutbu on 2009-06-12
Has Jaunty always behaved like this, or did this start to happen after installing some software, or following some guide?

---

### Post by kedmond on 2009-06-12
It was not always like this.  I haven't installed software...just run updates.  I think it began happening after a recent update.  I tried doing some how-to guides...but that didn't fix a thing.  Is there a way to reinstall everything that has to do with CPU scaling?

Jaunty's never been good about obeying what I selected from the applet menus, however.   I think that's why I began tinkering.  It was always locked into OnDemand...I think once I tried to change it, and now it's a mess.

-kedmond

---

### Post by unutbu on 2009-06-12
```
dpkg --get-selections | grep cpu
dpkg --get-selections | grep power
```
Please post the output.

---

### Post by kedmond on 2009-06-13
Output of first line:
cpudyn						deinstall
cpufreqd					install
cpufrequtils					install
libcpufreq0					install

Output of 2nd line:
gnome-power-manager				install
powermanagement-interface			deinstall
powermgmt-base					install
powernowd					deinstall
powertop					install

---

### Post by unutbu on 2009-06-13
In an attempt to reset your machine to "factory default" conditions, try purging the following packages:
```

sudo apt-get purge cpufreqd cpufrequtils libcpufreq0
```

Then try 

```
echo ondemand | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand | sudo tee /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

```
and see if the "ondemand" setting sticks. Since the above command might remove the applet you've been using, you can monitor the state of the scaling governor with this command:

Open a new terminal window and type:```

watch cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

This will poll the state of CPU0's governor ever 2 seconds.

---

### Post by kedmond on 2009-06-13
I don't want to jinx it...but I think it worked.

I have no idea what you made me do, but it seems to have done the trick.  I tried rendering a few images.  And then I rebooted, rendered some more.  I then used the applet to try different settings, then back to OnDemand.  It all worked!  Thanks so much!

-kedmond

---

### Post by pigphish on 2009-12-01
I think you hit the nail on the head with /etc/cpufreqd.conf 

I noticed the option defaults to performance 100-100%. 

I changed my profile for when in AC.

---

