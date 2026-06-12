---
title: "Cannot login to LXDE environment after reboot"
date: 2015-08-30
forum: Desktop Environments
---

### Post by mistcloud-misty on 2015-08-30
I am running Ubuntu 15.04 and due to having a very slow processor and slow ram I installed the LXDE environment many months ago with almost no problems. Today I did some updates, and because my computer was a bit slow after, I tried to restart. None of the leave options in the Openbox (LXDE environment) desktop worked - could not logout, reboot, shut down, suspend, hibernate, or anything. I would click on them and nothing would happen.

So I did a hard shut down and everything went fine until I tried to login. When I typed in my password, I would go past the login screen to a screen with lots of text (was only able to read the big red word ERROR) because I was sent right back to the login screen without knowing what the error was. When I went to login to the normal Ubuntu 3D desktop, everything worked fine.

I am not sure what was newly installed because I had installed many things previously (probably two weeks worth of updates) without rebooting my laptop so it could have been anything. 

Any way of fixing the login on LXDE because the basic Ubuntu 3D is extremely slow and barely runs right on my computer? I'm not sure where to check for logs, if any.

---

### Post by CantankRus on 2015-08-31
In the terminal run
```
sudo apt-get update
```
and post any errors.

---

### Post by mistcloud-misty on 2015-08-31
Well it looks like that found the problem, all the ones that failed to download are the ones it needs.

```
Err http://ppa.launchpad.net vivid/main amd64 Packages                         
  404  Not Found
Err http://ppa.launchpad.net vivid/main i386 Packages                          
  404  Not Found
Ign http://ppa.launchpad.net vivid/main Translation-en_US                      
Ign http://ppa.launchpad.net vivid/main Translation-en                         
Err http://ppa.launchpad.net vivid/main amd64 Packages                         
  404  Not Found
Err http://ppa.launchpad.net vivid/main i386 Packages                          
  404  Not Found
Ign http://ppa.launchpad.net vivid/main Translation-en_US                      
Ign http://ppa.launchpad.net vivid/main Translation-en                         
Fetched 842 kB in 20s (41.6 kB/s)                                              
W: Failed to fetch http://ppa.launchpad.net/sparkers/ppa/ubuntu/dists/vivid/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/sparkers/ppa/ubuntu/dists/vivid/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/vivid/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/unity-2d-team/unity-2d-daily/ubuntu/dists/vivid/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

