---
title: "Problem booting up FC6"
date: 2006-11-03
forum: Fedora/RedHat and derivatives
---

### Post by BWF89 on 2006-11-03
I installed FC6 on my computer yesterday but now whenever I turn on the computer after I get home from school it doesn't load up.

The opening loading screen with the show details comes up but after that I get an error that says

```
FATAL: error inspecting acpi-cpufreq/(libmodules/2.6.28-1.2798.fc6/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cppufreq.ko)
```

And after that it just boots up into command line and typing "startx" doesn't do make the GUI come up.

---

### Post by hey_ian on 2006-11-03
So you are running the PPC version of FC6, are not you? Because the system did not come to the run level which is required to start X window system, the command startx is completely useless. 

Are you sure that your Mac supports ACPI? If not, you will have to reinstall FC6 without ACPI. Which kernel is running currently on your FC6? 2.6.18 or did you install a different kernel version?

---

### Post by BWF89 on 2006-11-03
No, I'm running FC6 on a PC.

When I listed MacOSX and Fedora Core 6 in my sig I should have been more precice and noted that Fedora is running on a seperate computer.
> **hey_ian said:**
> Are you sure that your Mac supports ACPI? If not, you will have to reinstall FC6 without ACPI. Which kernel is running currently on your FC6? 2.6.18 or did you install a different kernel version?
I didn't change anything out of the box except installing a couple programs through YUM.

---

### Post by coffeecat on 2006-11-04
I'm getting the same or similar error message on bootup with FC6 on both a desktop and a laptop, but both seem to be running fine despite this. I haven't done a google search on this yet to find out what it means, but I think it's nothing to do with you not getting a GUI. 

A couple of suggestions. On my laptop I get a text login prompt for about 2 seconds, but if I leave it, the GUI login screen appears. Try waiting a bit.

The other thing worth checking is your /etc/inittab file. It should have a line that reads:

```
id:5:initdefault:
```but if it reads

```
id:3:initdefault:
```that would explain your problem, although I thought that even if you boot into runlevel 3, you should be able to start the GUI with startx. That being said, I have heard of the initdefault being mysteriously reset or set wrongly on installation, so it's worth checking. If you've got a 3 there, just change it to a 5. Backup your /etc/inittab file before editing it though. It's a critical system file.

---

