---
title: "vmware-player install or uninstall HELP!"
date: 2006-12-08
forum: Desktop Environments
---

### Post by shane2peru on 2006-12-08
Ok, it is in the repos, and should be a little more stable than that!  I ran```
sudo apt-get install vmware-player
```  Biggest mistake I have made so far!  Now, it is stuck!  It is not installed, and I can't uninstall it!  Every time I run apt-get it runs through it's dumb little install game, and fails everytime: ```
 sudo apt-get remove vmware-player
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  vmware-player
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  vmware-player
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 115047 files and directories currently installed.)
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
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I have tried ```
sudo aptitude purge vmware-player
``` no luck, I have tried ```
sudo apt-get install -f 
```  No go
I have tried ```
sudo ./vmware-uninstall.pl
```  Nothing - I have tried ```
 cd vmware-player-distrib/
shane@shane-laptop:~/vmware-player-distrib$ sudo ./vmware-install.pl 
A previous installation of VMware software has been detected.

Failure

Execution aborted.


``` as you can see, it failed.  I downloaded and unpacked the version from the web to try and install it so I could uninstall it as I read in another post.  I really need some help on this!](*,)   Why do I do things like this!?!?  Why is it every time I turn around it is something else?

Shane

---

### Post by declaration on 2006-12-09
I had the same problem as you and fixed it.

I did the purge command that you suggested but it told me that it couldn't delete a specific folder.

I just found this folder and deleted it manually, and now my new install will work.

---

### Post by shane2peru on 2006-12-09
Mine just ran through the install procedure again.  It was eternally stuck on trying to install it.  Anyway I tried to restore with a backup file that I had, turns out the back up was messed up, and long story short, re-install for #23.  [-( 

Shane

---

### Post by Muximori on 2006-12-18
I am having the exact same problem and it is driving me insane.

Is there any solution? I really don't wanna reinstall my os

---

### Post by erthian on 2006-12-22
Im having the same issue after trying Automatx2.  I usually like to do every thing by hand, and I guess this shows why.  Any way, just bumping this topic.  I cant even do updates because it tries to configure VMWare player...

---

### Post by shane2peru on 2006-12-22
I hope you find a solution!  I had to re-install.  I tried to install it be hand, as I don't use Automatix2 any longer, I have heard of too many problems.  

Shane

---

### Post by tylerdurden on 2006-12-25
anyone have a solution for this?

---

### Post by jurgen32 on 2006-12-25
Hey people.

I had the following prob.
I installed vmware-server and that went well. But after I installed vmware-player the sever version did'nt work anymore.
So I wanted the get rid of the player:evil: 
Hmmm, that did'nt went like I wanted.
But after some sniffing around in my system I found the solution.
Just reboot your system in the recoverymode.
Typ:
dpkg -r vmware-player
and if everything goes well.... wel then everything is going well ;) 

The problem was that there was a app. running in the background of the grapical environment.
By loggin in the textmode this problem was fixed:D 

Greeting and God bless,
Jurgen

---

### Post by wisedolphin on 2006-12-29
You can also try removing the vmware directory

sudo rm -R /etc/vmware/

then reinstall vmware server

---

