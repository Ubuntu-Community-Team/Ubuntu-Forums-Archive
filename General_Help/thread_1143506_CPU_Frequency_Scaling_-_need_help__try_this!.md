---
title: "CPU Frequency Scaling - need help?  try this!"
date: 2009-04-30
forum: General Help
---

### Post by Impact_666 on 2009-04-30
Update:  My initial post was flawed.  This revised posting seems to work correctly.

I'm not a Linux expert, but I hope this post helps people out.
If any of this info is wrong, let me know.



OS: Ubuntu Linux 9.04
Desktop: Gnome
Machine: Acer Aspire 3624 Laptop, Celeron M Processor



**How to enable CPU Frequency Scaling**
a. Open a terminal: <ALT-F2> run: gnome-terminal

b. Edit the /etc/modules file: sudo gedit /etc/modules

c. Add the following line to the end of this file:
p4_clockmod

d. Save file

*Module note:* p4_clockmod may not be best for your CPU.  I haven't verified the following list to be current.

powernow_k6 - for AMD K6 processors
powernow_k7 - for AMD K7 processors: Athlon, Duron, Sempron 32 bit
powernow_k8 - AMD K8 processors: Athlon 64, Turion 64, Sempron 64, Opteron 64
p4_clockmod - for Pentium 4, Celeron D, Pentium D, Celeron M
speedstep_centrino - for Pentium M, Core Duo, Core 2 Duo
acpi_cpufreq - generic driver

Thanks to Hugues Clouâtre for the above module info.  It was copied from his website, Techno Wizah.
Website: [http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html](http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html)



**Ubuntu automatically switches to "ondemand" governor after 60s delay**
Ubuntu starts with "performance" governor most likely to reduce boot-up time, then when it's safe to do so (60 seconds), start saving power.

To disable this, back up then delete the file /etc/init.d/ondemand

Backup: sudo cp /etc/init.d/ondemand newlocationpath
Delete: sudo rm /etc/init.d/ondemand



**Uncripple laptop-mode-tools**
Hey, thanks Ubuntu for messing this one up.

Uninstall the laptop-mode-tools and acpi-support packages supplied by Ubuntu, and install the Debian release instead.  Why?  Ubuntu's package is crippled.

a. Uninstall the Ubuntu laptop-mode-tools then quit Synaptic Package Manager.

b. Download the Debian laptop-mode-tools .deb file from [http://samwel.tk/laptop_mode/packages/debian](http://samwel.tk/laptop_mode/packages/debian)

c. Double-click on the Debian laptop-mode-tools, click "Install".

d. Re-load the Synaptic Package Manager, find and select laptop-mode-tools, then select Menu->Package->Lock Version.  This will prevent the accidental downgrade to the crippled version.

e. Reboot

*Note:* If you don't lock the version, or if you choose to perform by cli "sudo apt-get upgrade", you will revert back to the crippled version.  The version #'s are the same, but one is Debian, and the other is Jaunty.



**How to change the default governors**
a. Open a terminal: <ALT-F2> run: gnome-terminal

b. Edit the cpufreq.conf file:
sudo gedit /etc/laptop-mode/conf.d/cpufreq.conf

c. There are 3 lines (states) you can edit to change the governor:

   BATT_CPU_GOVERNOR=ondemand
   LM_AC_CPU_GOVERNOR=ondemand
   NOLM_AC_CPU_GOVERNOR=ondemand

What they mean:
BATT_CPU_GOVERNOR - running on batteries
LM_AC_CPU_GOVERNOR - in laptop-mode and running on AC
NOLM_AC_CPU_GOVERNOR - not in laptop-mode but is running on AC

Alter the lines to use one of the following governors:

performance
ondemand
conservative
powersave



**After you're finished**
a. Log out and log back in, or reboot.

b. If you want to verify the governor in-use, add the CPU Frequency Scaling Monitor applet to a Panel.



**CPU Frequency Scaling Monitor - Automatically saving governor**
If you manually change the governor via this applet, the setting won't be saved. The defaults will always be used.

I would like to learn how to write a script to save the governor for each of the 3 states (BATT, LM_AC, NOLM_AC).  It should be possible.  I think the only thing I can easily determine is what the current governor is, and of course that changes each time you change states.  I'd have to save the governor while running in each state, by performing the save during logout.  Is there a way to automatically call a script at logout?  If there is, let me know, and I'll take the time to write the script.  I'm good at learning on the fly.

Alternatively, I could write a GUI to make the changes easily.



**Issue**
Power events (plugging/unplugging the AC adapter) aren't captured when the laptop is in suspend/hibernation mode.

When you suspend/hibernate the laptop while running on AC (NOLM_AC mode), then unplug the AC, and resume on battery (BATT mode), the governor in use will be the one configured for NOLM_AC mode.



**Note for Ubuntu Linux v8.10**
I was able to enable CPU Frequency Scaling, but could never change the default governor - it was always using ondemand, except when I overrode it manually.  This might work for this version too.


I hope you found this useful.  Cheers!

---

### Post by AlexanderDGreat on 2009-08-01
Thank you, deleting /etc/init.d/ondemand worked for me. HP DV2000 Laptop. I also found a good article here: [http://www.pantz.org/software/cpufreq/usingcpufreqonlinux.html](http://www.pantz.org/software/cpufreq/usingcpufreqonlinux.html)
:D

---

### Post by Impact_666 on 2009-08-03
Hi!

You're welcome.

It was frustrating me that I had to visit around two dozen websites, and read through countless forum posts in order to find the information I needed.

This has helped at least one person, so it was worth it :)

---

### Post by AlexanderDGreat on 2009-08-15
@Impact_666 - your efforts are well-appreciated. Love it!

---

### Post by Neviar on 2009-08-23
This has helped me, too. Thanks!

Also, for those with NVIDIA graphics, [this]("http://ubuntuforums.org/showthread.php?t=828369") thread provides a script to automatically scale the GPU frequency based on battery status.

---

### Post by ahnise on 2009-11-24
I lost my /etc/init.d/ondemand file. (Followed these directions and did not back it up. Can someone post the contents of this file so I can fix my ondemand ?? Please please. hehe

---

### Post by Impact_666 on 2009-11-24
Sorry, I wrote this for an earlier version of Ubuntu.

For Ubuntu v9.10 I have:

-- Begin --
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
```

-- End --

I hope this helps.


My apologies if posting the code isn't permitted.  I only want to help the user.

---

### Post by X1R1 on 2009-11-25
What its the difference between the script you are posting here and the "Add to panel" -> CPU Frequency scaling monitor?

I added this to the panel and change this settings as needed.

---

### Post by Impact_666 on 2009-11-25
> **X1R1 said:**
> What its the difference between the script you are posting here and the "Add to panel" -> CPU Frequency scaling monitor?

I added this to the panel and change this settings as needed.


This script was added as of Ubuntu v9.04 I believe.

I think this was Canonical's logic:

Start Ubuntu as quickly as possible with the performance governor.
About 60 seconds after Ubuntu is loaded and the user is logged in, I think this script was being called to switch over to save power.

This was occuring automatically, and some of us didn't like that.  I only ever use this governor when I'm on battery, or don't care about sluggishness.

They did this in their quest to attempt to reduce the startup time, and then reduce power consumption, which is kinda stupid, since I rarely have the need to reboot my laptop - Linux isn't like Windows - it doesn't need to be rebooted every couple of days or weeks, and the ondemand governor makes my system sluggish at times.

---

### Post by Impact_666 on 2009-11-25
> **X1R1 said:**
> What its the difference between the script you are posting here and the "Add to panel" -> CPU Frequency scaling monitor?

I added this to the panel and change this settings as needed.

Sorry, to better answer your question....

The script is called automatically to force the computer to use the ondemand governor.

The cpu-freq applet is called manually so the user can force the computer to use whatever governor or frequency scaling is configured/supported by the processor.

---

### Post by X1R1 on 2009-11-25
I see...so I should force the computer to use the ondemand governor and if I need the processing power, switch back to the performance mode via the panel. 

Thanks for the answer!

---

### Post by Divider on 2009-11-25
what is the point of this topic exactly? all proccessor's that support scaling are automatically ondemand at all times. If your trying to remove that. And have 100% cpu usage, (get some good cooling) you can:

```
sudo apt-get remove powernowd
```

---

