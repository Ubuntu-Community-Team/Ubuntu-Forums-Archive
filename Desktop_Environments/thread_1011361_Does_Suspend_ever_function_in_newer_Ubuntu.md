---
title: "Does Suspend ever function in newer Ubuntu?"
date: 2008-12-14
forum: Desktop Environments
---

### Post by jwhiz on 2008-12-14
I have Hardy 8.04, and the ability to let my desktop PC sleep is important to me. I have tried many things, and have seen many posts, what I really don't understand is why the Ubuntu developers, and many in the community, seem so dismissive of this option on desktops - nor why anyone sticks with a laptop that either can't sleep, or can't resume properly from suspend, or that drops into hibernation when the user is active! That's nuts!
Here is what I've tried so far on my Mystery PC tower:
- in /etc/default/acpi-support, I set save_vbe_state=false, left acpi_sleep=true (!), tried acpi_sleep_mode=mem and =standby, use_dpms=false, post_video=false and even double_console_switch=true.
- updated grub
- removed, redownloaded, and tried to configure uswsusp (unfortuately, chose UUID thing as swap option, after numerous removals/reinstalls, can't get option back to change swap to the swap partition I set up when I installed Ubuntu - any suggestions as to where I can try that?); removed uswsusp
- have Nvidia GeForce card, suspect I need an older driver, how do I remove a graphics driver and still use the monitor? (yes, imagine, a newb question); I have also tried changing settings in /etc/x11/xorg.conf to add device option NvAGP and "1"
 - used synaptic to download powersaved, couldn't find it, so removed it
-used synaptic to see that I have pm-utils somewhere, but can't find it - is is just a set of commands used in a terminal? as a windows/mac user, i obviously prefer a gui command, preferably in gnome power manager/exit menu!!! but I will keep ubuntu around if I just need to 'manually' send it to sleep
-removed boinc. That isn't a good choice either, but wondered if settings were interfering somehow with hardware/Linux interface. Ideally, boinc runs for a while when I'm not using computer, then the system powers down and snoozes, then resumes without isuues as it does in every version of windows. 
Games means that i'll always have XP or something around, but would love to use Unixoids for every other purpose - my mac powerbook works fine (generally - heat means that I don't play games on it either). I'm interested in Linux OSes as desktop working enviroments, I get the work-in-progress thing, I don't get why there are so many problems with something I consider a basic function in so many newer Ubuntu versions. (Freespire worked fine, I'm feeling leery of it's unsupported status now).

To reiterate:
-can someone tell me how to switch graphics drivers?
-how do I persuade uswsusp to change swap partition (or find where it's loooking, and make appropriate redirection?)
-could Binc clients/manager be causing an problem?
-leery of bios upgrading, I've never done it on my own, and sleep options work fine in XP and Freespire - what options can i look at in bios to see what's needed in Ubuntu?
- does Debian itself have similar issues in newer versions? (and WHY!)

---

