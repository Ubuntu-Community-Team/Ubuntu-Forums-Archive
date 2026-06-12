---
title: "Make cpufreqselector Changes Survive Reboot?"
date: 2010-01-18
forum: Desktop Environments
---

### Post by klausner on 2010-01-18
I found how to make changes to Gnome's CPU Frequency Scaling Monitor applet without authenticating all the time [here]("http://ubuntuforums.org/showthread.php?t=1299820"). But I still have to change the settings every time I reboot! Is there a way to make the speed changes persistent?

---

### Post by mister_playboy on 2010-01-19
There have been several recent threads about this.  From one of them:

> **slnkez said:**
> Resurrecting an old thread here, but the easiest way I found on Karmic (9.10) was to install sysfsutils (editing rc.local didn't work, and especially doesn't work when you use concurrent=shell in rc).

sudo apt-get install sysfsutils

edit /etc/sysfs.conf and add to the end:
devices/system/cpu/cpu0/cpufreq/scaling_governor = conservative

Remove /etc/init.d/ondemand so that it doesn't set the cpu frequency to ondemand after a minute or so:

sudo mv /etc/init.d/ondemand /etc/init.d/ondemand.bak

It's useful to glance through the comments of /etc/sysfs.conf also.  You could do a lot of things with it without having to edit init scripts.

Replace conservative with which mode you want, and add a line for each CPU (cpu0,cpu1,etc.)  For example, I lock my dual-core to 1.87GHz with these lines at the end of the file(CPU speeds are in kHz):

```
devices/system/cpu/cpu0/cpufreq/scaling_governor = userspace
devices/system/cpu/cpu0/cpufreq/scaling_setspeed = 1870000
devices/system/cpu/cpu1/cpufreq/scaling_governor = userspace
devices/system/cpu/cpu1/cpufreq/scaling_setspeed = 1870000
```

---

### Post by klausner on 2010-01-19
Thanks. I thought I had done a thorough search here for an answer, but there are too many ways of phrasing this question. :redface:

---

### Post by klausner on 2010-01-19
Didn't work! Tried: > sudo apt-get install sysfsutils

edit /etc/sysfs.conf and add to the end:
devices/system/cpu/cpu0/cpufreq/scaling_governor = conservative

rebooted, both CPUs still come up set to Performance, not Ondemand as I had set in /etc/sysfs.conf. :(

---

### Post by tgeer43 on 2010-01-20
The frequency scaling applet includes a command line tool for setting the governor or cpu speed directly. Here's the method that I used to implement it.

Create a bash script similar to the following:
```
#!/bin/bash
cpufreq-selector -c 0 -g ondemand
cpufreq-selector -c 1 -g ondemand
exit 0
```One line for each CPU or core as specified by the -c option and with the governor of your choice as specified by the -g option. You can also set specific frequencies by using the -f option. See 'man cpufreq-selector' for addtional details.

Save the file somewhere and make sure that it's executable.

Now just add a new entry in System->Preferences->Startup Applications to run the script and you should be all set.

While your at it you can create similar scripts for the other governors or specific speeds that you CPU(s) supports. That way you can add aliases to them in your ~/.bashrc to quickly changes speeds/governors when working at the command line.

Hope this helps,

tgeer

---

### Post by klausner on 2010-01-20
> **tgeer43 said:**
> The frequency scaling applet includes a command line tool for setting the governor or cpu speed directly. Here's the method that I used to implement it.

Create a bash script similar to the following:
```
#!/bin/bash
cpufreq-selector -c 0 -g ondemand
cpufreq-selector -c 1 -g ondemand
exit 0
```

This is an interesting workaround. Unfortunately, the cpufreq-selector doesn't seem to terminate after setting the speed. So unless you put each line into the background, you never complete the script. :(

---

### Post by tgeer43 on 2010-01-23
> **klausner said:**
> This is an interesting workaround. Unfortunately, the cpufreq-selector doesn't seem to terminate after setting the speed. So unless you put each line into the background, you never complete the script. :(
So if you run that script from within a terminal it doesn't return to a command prompt? I can't think of a single reason why it would not. Works perfectly here or I wouldn't have suggested it.
What happens if you enter just the first line into a terminal?
```
cpufreq-selector -c 0 -g ondemand
```tgeer

---

### Post by klausner on 2010-01-23
> **tgeer43 said:**
> So if you run that script from within a terminal it doesn't return to a command prompt? I can't think of a single reason why it would not. Works perfectly here or I wouldn't have suggested it.
What happens if you enter just the first line into a terminal?
```
cpufreq-selector -c 0 -g ondemand
```tgeer

Nothing. Literally. If I run```
cpufreq-selector -c 0 -g ondemand
``` from the command line, nothing appears to happen, and I have to hit Ctl-C to get back to a prompt. Prefixing it with *sudo* has the same results.

---

### Post by tgeer43 on 2010-01-24
> **klausner said:**
> Nothing. Literally. If I run```
cpufreq-selector -c 0 -g ondemand
``` from the command line, nothing appears to happen, and I have to hit Ctl-C to get back to a prompt. Prefixing it with *sudo* has the same results.
Odd indeed. You say that nothing appears to happen but in your previous post you said that the script won't exit cleanly _*after*_ changing the speed. So does it change the governor or not?

At this point I'd try completely purging and reinstalling the following packages:

[LIST]
[*]gnome-applets
[*]gnome-applets-data
[*]libpanel-applets2-0
[/LIST]
And see if that clears anything up.
Out of curiosity, what is the exact model of your CPU?

tgeer

---

### Post by klausner on 2010-01-24
I may have been unclear in the first post. The script does not exit, because it hangs (presumably) at the first command. There is no effect on the CPU settings either way. 

FWIW, I [posted this]("https://bugs.launchpad.net/ubuntu/+source/gnome-applets/+bug/511794") as a bug.

The CPUs are Core2 Duo P8600s.

I'll try reinstalling the packages.

---

### Post by klausner on 2010-01-24
> **tgeer43 said:**
> At this point I'd try completely purging and reinstalling the following packages:

[LIST]
[*]gnome-applets
[*]gnome-applets-data
[*]libpanel-applets2-0
[/LIST]


Weird. That *seems* to have fixed it. But I'm going to wait a couple of days before marking the thread Solved.

Thanks for the help.

---

### Post by tgeer43 on 2010-01-24
> **klausner said:**
> Weird. That *seems* to have fixed it. But I'm going to wait a couple of days before marking the thread Solved.
And if so then don't forget to update your bug report too.

tgeer

---

