---
title: "D820 heating, no /proc/acpi/fan"
date: 2008-06-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MarilenCorciovei on 2008-06-22
Hello everyone, 

I am having a Dell Latitude D820 with a ubuntu hardy, kernel 2.6.24-19-generic and I have some heating problems. acpi -V constantly shows around 60C and sometimes it gets so hot I cannot use the touchpad. I have tried various things:
- playing with /proc/acpi/thermal_zone/THM/trip_points: this does not seem to work with this kernel anymore. It only shows: 
critical (S5):           126 C
- updated to A09 using the method described [here]("http://www.len.ro/work/tools/ubuntu-gutsy-on-a-dell-latitude-d820/bios-upgrade-with-no-windows-or-floppy")
- tryied to make dellfand work. It starts, turns the fan up then the fan stops, it starts again and then stops again. I guess dellfand turns the fan up and then something else turns it back on (the bios?)
- there is not fan in /proc/acpi/fan, the folder is empty

Any ideas?
Thank you,
Len

---

### Post by Diggs808 on 2008-06-28
Len,
I have a D820 also and you will need to install a program called i8k.  It is specifically for Dell and is located in the Repos.  What it does is allow you to set fan speeds.  And if you are using a program called gkrellm it will allow you to manually turn the fans on all in a GUI environment.  

This thread will tell you how to install the program.  

[http://ubuntuforums.org/showthread.php?t=842775](http://ubuntuforums.org/showthread.php?t=842775)

Best Regards!

Diggs

---

