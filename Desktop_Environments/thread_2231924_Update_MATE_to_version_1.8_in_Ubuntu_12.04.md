---
title: "Update MATE to version 1.8 in Ubuntu 12.04"
date: 2014-06-28
forum: Desktop Environments
---

### Post by ben_jetson2 on 2014-06-28
I currently have MATE 1.6 installed on my desktop machine running Ubuntu 12.04. I installed MATE using the directions on their website [here]("http://wiki.mate-desktop.org/download/#ubuntu"). The repositories for Ubuntu 12.04 do not appear to be updated to version 1.8, and it has been a few months since its release. All the directions that I can find online for installing MATE 1.8 are for Ubuntu 13.10/14.04. Is there another way to get the latest version of MATE (version 1.8) installed on my computer without upgrading?

--Ben

System Specifications:
[LIST]
[*]Compaq Presario SR2170NX 
[*]Dual Boot Ubuntu 12.04/Windows 7 Pro 32bits 
[*]2GB RAM 
[/LIST]

---

### Post by Vladlenin5000 on 2014-06-28
Isn't it amazing what we can find with just a simple Google search?

[http://www.webupd8.org/2014/03/how-to-install-mate-18-in-ubuntu.html](http://www.webupd8.org/2014/03/how-to-install-mate-18-in-ubuntu.html)

---

### Post by ben_jetson2 on 2014-06-28
I found this same article a few hours ago. I follow the guide, adding the repository, running the comand in the second step, and then running "sudo apt-get update" and towards the end of the terminal, it says:

```
W: Failed to fetch http://repo.mate-desktop.org/archive/1.8/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Running the final step of that guide, installing the packages, I get this:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
mate-core is already the newest version.
mate-desktop-environment is already the newest version.
mate-notification-daemon is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
```

After rebooting, I still have MATE 1.6

[IMG]http://i.imgur.com/wKqKsVX.png[/IMG]

Is there something that I missed or something that I did incorrectly?

---

### Post by Vladlenin5000 on 2014-06-28
This note was there all along

> **Note that the official MATE 1.8 Ubuntu repository only supports Ubuntu 14.04 and 13.10!**

---

### Post by ben_jetson2 on 2014-06-28
My question was about how to install MATE 1.8 on Ubuntu 12.04. Is there another way to install MATE 1.8 on Ubuntu **12.04** without using the repository mentioned above or upgrading Ubuntu?

---

### Post by Vladlenin5000 on 2014-06-28
Apparently not but perhaps you could ask the developers.

---

### Post by ben_jetson2 on 2014-06-28
I will ask on the official MATE forum to see if the developers plan to update the repos for 12.04. Thank you for your assistance and quick replies. :)

---

### Post by tgalati4 on 2014-06-29
You can probably build MATE 1.8 on a 12.04 system, but there will be some libraries that are needed that are newer than what you have in 12.04.  It's probably a 50/50 chance that upgrading those libraries will break your base 12.04 system.  The fixes will be hard to find because you will be a population of 1 that has this configuration.

What killer feature do you have to have in 1.8?  What is lacking in version 1.6 that bothers you?

The Agony Units of trying to build MATE 1.8 on a 12.04 system are probably higher than a fresh installation of Linux Mint MATE 17 (which is built on 14.04).  Expect breakage either way.

---

### Post by ben_jetson2 on 2014-06-29
OK, so the easier path is to use LM 17 with MATE or to upgrade Ubuntu. The feature that I want from MATE 1.8 is window snapping and the ability to move a window between my two monitors with a keyboard shortcut. I'll try to upgrade Ubuntu first before switching to LM. I usually end up doing a fresh insall anyway becuase the upgrades seem to cause trouble. The last upgrade I tried was on my laptop from 12.10 to 14.04, and it failed to boot afterwards.
Thanks for your help! :)
--Ben

---

### Post by tgalati4 on 2014-06-29
Expect breakage.

---

### Post by ben_jetson2 on 2014-06-30
I ended up installing Linux Mint 17 MATE, which has 1.8 preinstalled. Since I had /home on a seperate partition, it didn't take long at all to get back up and running. Thanks to everyone for the advice. :)

---

