---
title: "monitor/system won't wake up.."
date: 2005-03-11
forum: Desktop Environments
---

### Post by wxlidar on 2005-03-11
I am running Warty and am having a problem with the machine not waking up. At the end of the work day, I lock my screen and head out. Periodically, the following morning the screen is black (no signal) but the system seems to be running. The fans are running and the power light it illuminated. It sounds like the HD is still spinning. The mouse has power too. However, nothing I do will wake up the machine. Moving the mouse or any key combinations do not work. Today it did it while I was gone from my machine for less than one hour.

Power management is disabled in the screensaver preferences. My screensaver is set to blank after 5 minutes, cycle after 10 minutes, and lock the screen after 10 minutes. I can not find any power saving settings in my BIOS. 

I've searched the forums and found references to hibernation and sleep problems. What I did find seems to be in reference to laptops. This is occuring on a ~2 year old Pentium based desktop. It seems to be video-only.

Any suggestions? Can this be ACPI related? There seems to be plenty of ACPI entries in my messages log file but it seems to load just fine.

Thanks,
Dave

---

### Post by alastair on 2005-03-11
I have had this happen to me in the past on a different distribution. Try disabling the screensaver and see if that helps (perhaps just turn the monitor off). My problem seemed to be OpenGL screensaver based i.e. graphics driver.

---

### Post by wxlidar on 2005-03-14
Thanks Alastair for the suggestion. I'll give it a try.

Dave

---

