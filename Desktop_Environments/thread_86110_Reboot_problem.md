---
title: "Reboot problem"
date: 2005-11-04
forum: Desktop Environments
---

### Post by art on 2005-11-04
Well, I installed breezy again, this time from the scratch. I seem to have gotten everything the way I want it to be. The only problem I have is the reboot. When I reboot from Ubuntu, after computer turns off, then the Toshiba splash screen appears, after which the Grub should show up. But instead the computer powers off (the power button goes off) for a fraction of a second and boots back up, again Toshiba splash, and continues normally:confused:  This doesn't happen when rebooting from Windows... And it wasn't the case with Hoary. I am really afraid of this messing up my motherboard. Any ideas? 
Thanks a lot!

---

### Post by Kyral on 2005-11-04
So basically it does a really quick complete shutdown and into a cold boot?

Actually that sounds like what happens when I reboot ( Custom built desktop machine)

I wouldn't worry about the Mobo. As long as you aren't suddenly cutting power it shouldn't mess anything up.

---

### Post by art on 2005-11-04
Hey, thanks for a reply kyral!
Yeah, but it starts booting up, then powers off which to me sounds like "suddenly cutting power"... And after yesterday's shut down today it wasn't even booting up when I pressed the power button. Only when I removed the battery and reinserted it back it started working... I got my motherboard fried twice with FC3, and one of the main reasons I was so much in love with Ubuntu was that it was not frying my MB:) What do you think?

---

### Post by art on 2005-11-04
So nobody has experienced this, or any ideas as to what can it be?
I am in a really bad mood because of this...

---

### Post by Kyral on 2005-11-04
Hey I'm not the guy to ask about power switches. My case is screwed up so I have to ducttape the power button down to keep it on ;P

---

### Post by aysiu on 2005-11-04
This shouldn't make a difference, but does it do the same thing if you reboot from the terminal? ```
sudo reboot
```

---

### Post by art on 2005-11-04
absolutely the same result...
I would like to restate that this happens only when rebooting from breezy, doesn't happen from windows, and was not happening in hoary. Maybe it's a bug in kernel, or ACPI?

---

### Post by bigc on 2005-11-23
I have a similar problem, but it also hapens when powering down. The system goes down normaly, but it doesn't power off and i have to power off on the switch.

Does anyone have any ideas??

---

### Post by dcstar on 2005-11-23
[QUOTE=bigc]I have a similar problem, but it also hapens when powering down. The system goes down normaly, but it doesn't power off and i have to power off on the switch.

Does anyone have any ideas??[/QUOTE]
I have experienced these sort of things and had work-arounds with kernel boot strings that disable ACPI etc.

Try updating to the latest kernel (released yesterday), or have a look at this thread for the boot options:

[http://ubuntuforums.org/showthread.php?t=2620](http://ubuntuforums.org/showthread.php?t=2620)

---

### Post by art on 2005-11-23
Well the new kernel didn't help me, and the thing is the problem wasn't there with hoary, so I don't think it's related to hardware, ACPI does work on this thing...

---

