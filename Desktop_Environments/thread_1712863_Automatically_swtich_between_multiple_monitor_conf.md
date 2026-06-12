---
title: "Automatically swtich between multiple monitor configurations?"
date: 2011-03-23
forum: Desktop Environments
---

### Post by mshiltonj on 2011-03-23
I have a laptop that I use in three environments with different monitor setups.

1) At work, I have a 1280x1024 second monitor.
2) At home, I have a 1920x1080 second monitor.
3) In meetings and other places I have no second monitor.

Whenever I switch between these setups, which is at least several times each day, I have to manually change the monitor configuration. I use the nvidia-settings tools. 

Granted, it only takes a few seconds. Is there a way to make the system smart enough to automatically detect when a monitor is added or removed, know *which* monitor is attached, and reconfigure the resolution and monitor layouts the way I want them?

Thanks.

---

### Post by Krytarik on 2011-03-23
Generally it isn't impossible to achieve that, but it requires a certain degree of co-operation between the nvidia driver and xrandr, and a bit luck.

You could set up a script which
1.) checks with "hwinfo --monitor" if certain "Unique ID"s of monitors are present (1)
2.) sets the output resolution of the present monitors with xrandr (2)
3.) arrange the monitor outputs with xrandr

You could run those script
- via the startup script of GDM (3)
- via "Startup Applications"
- manually with a launcher

(1)
- "hwinfo" is in the official repos
- [http://manpages.ubuntu.com/manpages/maverick/en/man1/grep.1.html](http://manpages.ubuntu.com/manpages/maverick/en/man1/grep.1.html)
- [http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html)
(2)
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
[http://manpages.ubuntu.com/manpages/maverick/en/man1/xrandr.1.html](http://manpages.ubuntu.com/manpages/maverick/en/man1/xrandr.1.html)
(3)
[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20commands%20in%20kdm/gdm%20startup%20scripts](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20commands%20in%20kdm/gdm%20startup%20scripts)

Good luck and don't hesitate to ask for help!

---

