---
title: "Ubuntu 16.04 Beta to Ubuntu 16.04 Full"
date: 2016-03-16
forum: Desktop Environments
---

### Post by ricardo-gcclinux on 2016-03-16
So here is a question, if I download the daily 16.04 LTS Beta as it is today and install it on my Desktop/Laptop will it stay up to date once the full version is released and automatically become full version with a few patches or will I need to re-install the whole system with the latest Full version once released?

Many Thanks

---

### Post by PaulW2U on 2016-03-16
> **ricardo-gcclinux said:**
> So here is a question, if I download the daily 16.04 LTS Beta as it is today and install it on my Desktop/Laptop will it stay up to date once the full version is released and automatically become full version with a few patches or will I need to re-install the whole system with the latest Full version once released?
Ubuntu, unlike the flavours, hasn't released a beta yet. You can find the latest daily build at [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/).

An alpha or beta release is just a snapshot of development so far. As soon as it's released then subsequent updates make it out of date.

If you continue to use and update any pre-release installation then in theory you will end up with the same as the final release. There may be some "crud" leftover from changes that have been reverted but a full re-installation should not be necessary. Of course you would be installing something that has not yet been fully tested. You may well encounter problems before the release date of April 21st and find that another re-installation is required.

The Ubuntu [Release Schedule]("https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule") gives the relevant dates.

---

### Post by ricardo-gcclinux on 2016-03-16
Thanks for the update, I have run a $sudo apt-get upgrade today and loads new packages got updated, I have noticed a coule of issues like with the gnome calendar for example it crashed, not a problem I am only playing with it. Anyway 16.04 so far seem to be the nices realease so far. I did install a couple of additional packaged to drop the unity menu to the bottom os the screen and that made it even perfect, I currently run ubuntu 14.04 with cinamon dekstop at the moment as I don't like the left hand side menu, but now with the possibility of putting at the bottom of the screen I will be keeping unity :-)

---

### Post by grahammechanical on 2016-03-16
Once Ubuntu 16.04 has been released you might want to run

```
sudo apt-get update
sudo apt-get upgrade
```

You may see a list of packages that are installed and no longer needed. This will remove them

```
sudo apt autoremove
```

Regards.

---

### Post by oldfred on 2016-03-16
There also are a lot of logs and old packages. Perhaps old kernels.
So best to do a full houseclean.
I usually just reinstall which is then a full houseclean but have exported list of apps and /home backup so easy to restore.

       RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

 Caution deborphan will delete anything you manually installed. See comment: 
 Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

---

