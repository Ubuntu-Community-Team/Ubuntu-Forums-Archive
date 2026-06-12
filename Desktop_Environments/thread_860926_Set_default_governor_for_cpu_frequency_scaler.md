---
title: "Set default governor for cpu frequency scaler"
date: 2008-07-16
forum: Desktop Environments
---

### Post by goodbadwolf on 2008-07-16
Hi. How do i set the default governor of the cpu freq scaling monitor to remember the last used setting to be restored on boot ? It changes back to ondemand after each boot. I use Ubuntu 8.04

---

### Post by squaregoldfish on 2008-07-16
You can put the command you need in /etc/rc.local, which is run at every boot. If you want to use the powersave governor, adding the following line will do the job:

```
echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

If you have more than one CPU or core, you'll have to repeat the process for cpu1,cpu2 etc.

Steve.

---

### Post by jesusdemontreal on 2008-08-16
I would suggest reading this post [http://ubuntuforums.org/showthread.php?t=541794]("http://ubuntuforums.org/showthread.php?t=541794"). You don't need to run a command at each boot, you can change the default.

---

### Post by slnkez on 2010-01-12
Resurrecting an old thread here, but the easiest way I found on Karmic (9.10) was to install sysfsutils (editing rc.local didn't work, and especially doesn't work when you use concurrent=shell in rc).

sudo apt-get install sysfsutils

edit /etc/sysfs.conf and add to the end:
devices/system/cpu/cpu0/cpufreq/scaling_governor = conservative

Remove /etc/init.d/ondemand so that it doesn't set the cpu frequency to ondemand after a minute or so:

sudo mv /etc/init.d/ondemand /etc/init.d/ondemand.bak

It's useful to glance through the comments of /etc/sysfs.conf also.  You could do a lot of things with it without having to edit init scripts.

---

### Post by blueshiftoverwatch on 2010-01-12
> **slnkez said:**
> Resurrecting an old thread here, but the easiest way I found on Karmic (9.10) was to install sysfsutils (editing rc.local didn't work, and especially doesn't work when you use concurrent=shell in rc).

sudo apt-get install sysfsutils

edit /etc/sysfs.conf and add to the end:
devices/system/cpu/cpu0/cpufreq/scaling_governor = conservative

Remove /etc/init.d/ondemand so that it doesn't set the cpu frequency to ondemand after a minute or so:

sudo mv /etc/init.d/ondemand /etc/init.d/ondemand.bak

It's useful to glance through the comments of /etc/sysfs.conf also.  You could do a lot of things with it without having to edit init scripts.
Thanks for posting that. I wonder what the odds are that you posted that only 19 hours before I searched for it on the forums? My 4 cores are now happily chugging along in performance mode without me having to manually adjust it every time I start a new session.

You'd think they'd put an option in the CPU Frequency Scaling Monitor Gnome panel applet that would allow you to save your settings so they would be enabled for your next session though. It would make it easier for newbies to scale their CPU's without having to edit text files.

---

### Post by slnkez on 2010-01-13
> **blueshiftoverwatch said:**
> Thanks for posting that. I wonder what the odds are that you posted that only 19 hours before I searched for it on the forums? My 4 cores are now happily chugging along in performance mode without me having to manually adjust it every time I start a new session.

You'd think they'd put an option in the CPU Frequency Scaling Monitor Gnome panel applet that would allow you to save your settings so they would be enabled for your next session though. It would make it easier for newbies to scale their CPU's without having to edit text files.

Oh, by the way, I found CPU governor defaults to performance if you set CONCURRENT=shell in /etc/init.d/rc (some people like to do that to speed up boot time).  Thus meaning, this solution only works when CONCURRENT=none

Anyway, you're right, having the settings stick from the applet would be more user-friendly.  I think in trying to make things too simplified, they confuse even seasoned users of other distros like Slackware.  :P

---

### Post by blueshiftoverwatch on 2010-01-14
I just increased the clock multiplier from auto (17) to 17.5 in my BIOS. Increasing the clock speed from 3.4 to 3.5GHz. For some reason now I get an error message when I start up my computer telling me that CPU frequency scaling is not longer working.

"*You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.*"

I guess changing from auto to a set multiplier takes away the ability change it in the OS and keeps it automatically scaled at X speed at all times. Not that it matters, if my frequency scaling is set to performance mode I don't really need a gauge to tell me that what frequency every core is clocked at.

So, instead of having to edit that text file like you posted how I could have just modified the clock multiplier on the BIOS.

---

### Post by mister_playboy on 2010-01-14
This is useful for Folding@Home, since that program won't keep the Processor speed maxed in "on demand" mode.

---

### Post by L815 on 2010-01-14
> **blueshiftoverwatch said:**
> Thanks for posting that. I wonder what the odds are that you posted that only 19 hours before I searched for it on the forums? My 4 cores are now happily chugging along in performance mode without me having to manually adjust it every time I start a new session.

You'd think they'd put an option in the CPU Frequency Scaling Monitor Gnome panel applet that would allow you to save your settings so they would be enabled for your next session though. It would make it easier for newbies to scale their CPU's without having to edit text files.

Oddly enough, I came across this at the perfect time (just now). I remember being able to change the option in gconf-editor, but there seems to be no option anymore.

This should really be an option somewhere. It's great you can change it, but I'd prefer it to remember my setting!

---

### Post by acejase66 on 2010-01-23
> **slnkez said:**
> Oh, by the way, I found CPU governor defaults to performance if you set CONCURRENT=shell in /etc/init.d/rc (some people like to do that to speed up boot time).  Thus meaning, this solution only works when CONCURRENT=none

This handy piece of info solved something that's been bugging me for a while.  I'd enabled the CONCURRENCY=shell boot tweak prior to installing the CPU Frequency Scaling Monitor and then couldn't work out how to set CPU scaling to Ondemand by default.  I've now set it back to CONCURRENCY=none, rebooted, and the problem's solved.

Thanks heaps.

---

### Post by kevr on 2010-02-07
To set any default cpufreq governor by default on boot:

**sudo cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors**

Displays all your possible scaling governors

Next,

**gksudo gedit /etc/init.d/ondemand**

Will open this file:
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          ondemand
# Required-Start:    $remote_fs $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Set the CPU Frequency Scaling governor to "ondemand"
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

case "$1" in
    start)
        start-stop-daemon --start --background --exec /etc/init.d/ondemand -- background
        ;;
    background)
    sleep 60 # probably enough time for desktop login

    for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
    do
        [ -f $CPUFREQ ] || continue
        echo -n ondemand > $CPUFREQ
    done
    ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```Find where it says "**echo -n ondemand > $CPUFREQ**" on line 27 and replace **ondemand** with the available scaling governor you wish to use. For example, "**echo -n performance > $CPUFREQ**" (without quotes of course). After modifying, save and close gedit then proceed to reboot. You should have all your cores on the desired scaling governor at boot now.

Of course, you can also set /etc/rc.local with some script lines to execute this on boot. Personally for me, /etc/rc.local did not execute the scripts I tried out, so I continued on to editing the ondemand file which is loaded up before rc.local is.

Have fun. ;)

---

### Post by NRDNick on 2010-02-21
Thanks kevr and to who ever figured that out, works like a charm.

---

### Post by krcabrer on 2010-02-22
Hi Ubuntu users:

I got a phenom II x4 955 BE, and I am using de "cpu frequency scaler".

What is the best setting for a system that make simulations, and
math calculation several times a week?

A newbee question: Is this a overclocling setting?

Where can I find good overclocking setting por especific goals?

Thank you for your help.

Kenneth

---

### Post by aamr on 2010-03-05
A much easier way is to set the frequency you need via the CPU Frequency Scaling applet (per CPU core) and just renaming or removing the /etc/init.d/ondemand, e.g. "sudo mv /etc/init.d/ondemand /etc/init.d/ondemand.bak" I've tried it and it's working well.

---

### Post by deeexx on 2010-05-10
Renaming the file /etc/init.d/ondemand did not work for me on 10.04
I also tried removing the execute attribute (eg. chmod -x ondemand) and that also didn't work. My install is pretty much default so far although not freshly installed but upgraded from 9.10.
kevr's method above saying to change the word "ondemand" to something else like "conservative" did however work for me. It just doesn't seem to be a very neat solution to have a file called ondemand doing something else.
I would appreciate having a better, or even a gui solution to setting the default governor.

---

### Post by spikyjt on 2010-09-01
kevr's edit of /etc/init.d/ondemand works a treat. I took it a stage further and set up /etc/default/cpu_governor to contain:
```
GOVERNOR=performance
```
and added the following to /etc/init.d/ondemand (in the appropriate places:
```

GOVERNOR=ondemand
. /etc/default/cpu_governor

               echo -n $GOVERNOR > $CPUFREQ


```
Of course the naming of the script is not ideal, as pointed out by deeexx. By all means have the governor set to ondemand by default (after all, that is what Intel recommends), but providing a standard way to set an alternative would be nice. The init script could be renamed to cpu_governor I feel, with the /etc/default/cpu_governor file added as standard, with a commented list of appropriate possibilities.

---

### Post by kevr on 2010-10-29
> **deeexx said:**
> Renaming the file /etc/init.d/ondemand did not work for me on 10.04
I also tried removing the execute attribute (eg. chmod -x ondemand) and that also didn't work. My install is pretty much default so far although not freshly installed but upgraded from 9.10.
kevr's method above saying to change the word "ondemand" to something else like "conservative" did however work for me. It just doesn't seem to be a very neat solution to have a file called ondemand doing something else.
I would appreciate having a better, or even a gui solution to setting the default governor.

If you want, you could create a gui or a startup script that sed's the ondemand file to a hash file then replaces the ondemand file.

man sed

---

### Post by l0uismustdie on 2010-11-21
This seems like a good forum to link this question to.  I have been experiencing trouble getting my /etc/init.d/ondemand script to run at bootup.  I have posted a bunch of information on this other thread but no one seems to want to provide useful information there:
[http://ubuntuforums.org/showthread.php?t=1582422](http://ubuntuforums.org/showthread.php?t=1582422)

Seems like those posting on this thread might have an idea about this.

Thanks.

---

### Post by Infil on 2011-03-11
My CPUs are set to "performance" on boot. It wasn't like this but became  this way after I installed and then removed cpufreqd. I want it to be set to "ondemand". My /etc/init.d/ondemand actually says "echo -n ondemand > $CPUFREQ" but still the CPUs are set to "performance". 

Can anyone help?

EDIT: Nevermind. I read that on boot CPUs stay in "performance" for 60 seconds then drop down to "ondemand". This is the case here as well.

---

### Post by nmyrick on 2011-12-19
Another way to change the default frequency scaling without deleting any files, or running any additional code at startup, is to run nautilus as root and edit the ondemand file in /etc/init.d.

To run nautilus as root, open a terminal and enter: sudo nautilus
after that, you will be prompted for your login password.

The go to /etc/init.d and open 'ondemand'

With the file open, go to the command shown below, delete 'ondemand' and enter the default scaling you want.  DO NOT CHANGE THE FILE NAME WHEN SAVING.

do
        [ -f $CPUFREQ ] || continue
        echo -n ondemand > $CPUFREQ
    done

---

