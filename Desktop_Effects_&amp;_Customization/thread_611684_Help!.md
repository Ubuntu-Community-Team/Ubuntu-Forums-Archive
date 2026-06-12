---
title: "Help!"
date: 2007-11-13
forum: Desktop Effects &amp; Customization
---

### Post by psycho5 on 2007-11-13
I am running Ubuntu 7.10 build, everything was running silky smooth. I had desktop effects going, Compiz working fine and well with my Binary Drivers for Nvidia 8600GTS.

Then I came across this thread on how I can put different wallpapers on each side of the cube: 
[http://ubuntuforums.org/showthread.php?t=600909](http://ubuntuforums.org/showthread.php?t=600909)

I uninstalled compiz first (as it recommends) through terminal window in ubuntu and ran the script. 

Got error on the first task in the script, file not found to backup... 

went to the second step, configuring prerequisites, but nothing happened, no network activity. I aborted it and thought a reboot would help since after uninstalling compiz my effects were still on.

Here's where everything went downhill. I can't boot back in GUI mode anymore, I get that safe graphics mode. I can't select default display anymore. I try selecting it, I just get a beep after I hit Test or Okay. 

I am not sure why but I think because I've modified the file 
 /etc/default/linux-restricted-modules  when I installed the Binary drivers

and changed DISABLED_modules = " " to "nv nvidia_new"

Before running that script for the cube,  everything was fine. Can anyone guide me how to revert back how things were before I ran the script? I think I messed up my system.

---

### Post by psycho5 on 2007-11-13
Nevermind ppl :) solved it on my part, Had a backup of the linux-restricted-common and so I reinstalled the drivers again.

---

