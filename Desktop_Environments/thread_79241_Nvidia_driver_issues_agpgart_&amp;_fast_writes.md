---
title: "Nvidia driver issues: agpgart &amp; fast writes"
date: 2005-10-19
forum: Desktop Environments
---

### Post by dangerous666 on 2005-10-19
I cannot say it's really a problem, cause everything is working properly.

In Hoary, I used to install the latest official nvidia drivers...After that, I could realize that the use of nvida's agp driver(nvidia_agp) brought some perfomance improvements.. So, the process was to prevent agpgart to load, putting it in /etc/hotplug/blacklist/ (in fact i put only via-agp, which calls agpgart), and editing some config files like putting nvidia_agp and nvidia in /etc/modules/ and adding nvidia NVreg_EnableAGPFW=1 NVreg_EnableAGPSBA=1 to /etc/modutils/nvidia-kernel-nkc.. So It just worked fine in hoary, I could get the nvidia driver using the nvidia's gart, no kernel's agpgart loaded and fastwrites and SBA enabled.

But in Breezy, this is not working. I did the same process, but agpgart is always loaded and I have fast writes disabled.. I did exactly the same process I used to do in Hoary... I have the nvidia driver using Nvidia's agp (I can see it in /proc/driver/nvidia/agp/status) but I don't know why, agpgart is loaded(how? it is in the blacklist, in breezy i add via-agp and agpgart  to blacklist), and lsmod says that agpagat is being used by nvidia_agp and nvidia... So this is the problem.. I have no problems whith 3d apps, but this thing is a bit strange...

Need help

Thanx!

---

### Post by Takis on 2005-10-19
This stuff is totally over the top of my head. I guess though that even if you blacklist a module, if another module that you haven't blacklisted requires it, the module will be loaded. This really probably needs a dev to answer.

---

### Post by dangerous666 on 2005-10-20
[QUOTE=Takis]This stuff is totally over the top of my head. I guess though that even if you blacklist a module, if another module that you haven't blacklisted requires it, the module will be loaded. This really probably needs a dev to answer.[/QUOTE]

:(

---

### Post by ChrisNiemy on 2007-03-10
Although this thread is outdated, someone may find it again with the search function. So here's the solutuion:

just edit your 
/etc/modprobe.d/nvidia-kernel-nkc
in the following way:
for example the original looks like this:```

alias char-major-195* nvidia
```

add a new line "options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1", so it will look like this:
```
alias char-major-195* nvidia
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1
```

If /etc/modprobe.d/nvidia-kernel-nkc unlileky does not exists, just create it and paste the 2 lines in it and save.

Of course you could choose only one of the two options, depending on what your board and card supports. Otherwise only features, which are supported by both will be enabled, so you won't mess anything up, if a feature is not supported. (e.g. my card does support SBA and FW, but my board-host-bridge only supports SBA.)
What you board does support you can get to know by: 
```
cat /proc/driver/nvidia/agp/host-bridge
```
What you card does support:
```
cat /proc/driver/nvidia/agp/card
```

No need for editing /etc/modules.


After Reboot, check if it succeeded with:
```
cat /proc/driver/nvidia/agp/status
```



PS: More detailed in this thread:
[http://www.ubuntuforums.org/showthread.php?t=140989&highlight=nvidia+side+band](http://www.ubuntuforums.org/showthread.php?t=140989&highlight=nvidia+side+band)

---

