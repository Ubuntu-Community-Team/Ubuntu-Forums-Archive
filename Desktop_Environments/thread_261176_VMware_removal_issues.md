---
title: "VMware removal issues"
date: 2006-09-19
forum: Desktop Environments
---

### Post by odweaver on 2006-09-19
My issue with vmware is that whenever I try and do something in terminal it asks me if I want to overwrite some vmware virtual ethernet files, after I finish the process it gives me an error and tries to start over, which causes problems.
When I try and uninstall vmware through the add/remove menu I recieve this error: ```
odweaver@odweaver-desktop:~$ sudo apt-get remove vmware-player Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  vmware-player
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
odweaver@odweaver-desktop:~$ sudo apt-get remove vmware-player
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  vmware-player
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 32.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 113290 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Anduu on 2006-09-19
Try booting into recovery mode so vmware doesn't get loaded and try an apt-get remove from there.

---

### Post by odweaver on 2006-09-20
Meh, already reformatted and didn't install the package, now I'm just setting up fluxbox, thanks for the advice though.

---

### Post by olifhar on 2007-01-18
Just for informational purposes, for anyone else with the same issue who hasn't given up and reinstalled out of utter frustration...

The same thing happened to me, and I solved it by manually listing then killing all the processes, and then running apt-get remove.

```
ps -ef | grep vmware
...(some output)...
kill -9 (some process' pid)
...(repeat for all processes listed)...
sudo apt-get --purge remove vmware-player

```

---

### Post by TrashmanL on 2007-08-16
My problem is not quite as extreme. I installed VMWare Player, then realized I needed the server version for what I wanted to do. When I tried to install VMWare Server, I got this error:

If you installed it from the VMware website, please remove it by running vmware-uninstall.pl before proceeding.

If it was installed through Ubuntu, you must purge (completely remove) the old package.

So, I went used the Synaptic Package Manager, searched for VMWare and selected the "Mark for Complete Removal" (the same as apt-get --purge remove) option for everything VMWare related that was still installed. I restarted, then attempted to install VMWare Server, and still got the same error!

I found this thread, and tried what you suggested. When I did ps -ef grep vmware however, nothing came up (well, the ps command I just made came up, it killed my terminal window when I killed it, of course). I then just did a ps -ef (as su) and looked through the list. I still did not see anything vmware related running. 

I also tried using apt-get --purge remove, just in case there were differences, but it reported that vmware-player was not installed so it couldn't remove.

The only sign I have that something related to VMWare still exists, is when I go to the System Menu/Administration/Services, the "Virtual Machine manager (vmware-player)" is still listed. 

What am I missing? How can I get VMWare-server to install?

---

### Post by lahdo on 2008-06-13
Error: When I try to install VMware Server, I get the following error message: 
    A previous installation of a VMware product has been detected.
    If you installed it from the VMware website, please remove it by running vmware-uninstall.pl before proceeding.
    If it was installed through Ubuntu, you must purge (completely remove) the old package.

Solution: First of all, unsure that you "Completely Removed" vmware-player/vmware-server and all its modules. To unsure that, run the following command: 
    sudo aptitude purge vmware-server vmware-player vmware-tools-kernel-modules

If you still keep getting the above error, run the following command: 
    sudo rm -r /etc/vmware*

Source:  [http://ubuntuforums.org/showthread.php?t=491854](http://ubuntuforums.org/showthread.php?t=491854)

---

