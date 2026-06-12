---
title: "Latest Software Update Wont Boot"
date: 2023-01-19
forum: Desktop Environments
---

### Post by scpatl4now on 2023-01-19
I ran the daily security updates today which required reboot, and system showed splash screen then black page with blinking curser where it hangs.  I was able to boot by going to recovery and changing permissions (that should not have been changed).  I saw this solution in another thread from today

chmod 755 /
chmod 755 /bin
chmod 755 /lib
chmod 755 /lib64

now that I have logged in it is offering a security update for a bunch of NVIDIA updates that are unchecked as well as Ubuntu base that are not checked
The only thing checked is 2 Linux kernel options to remove NVIDIA modules/ signature modules for 5.15.0-58

I don't want to run this until I know it wont bork my system.  Any suggestions?

Disregard this entry as I have submitted a more detailed thread in general help since that is more appropriate

[https://ubuntuforums.org/showthread.php?t=2483064](https://ubuntuforums.org/showthread.php?t=2483064)

---

