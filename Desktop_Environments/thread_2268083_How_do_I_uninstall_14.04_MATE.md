---
title: "How do I uninstall 14.04 MATE?"
date: 2015-03-06
forum: Desktop Environments
---

### Post by PopsTheSailor on 2015-03-06
I installed Ubuntu MATE 14.04 using the Install CD that was prebuilt with MATE. I need to completely uninstall the MATE UI. How do I do that?

---

### Post by kurt18947 on 2015-03-06
If Ubuntu MATE is installed in a separate partition, can you simply delete the partition then update grub to remove ubuntu mate from the list? I don't know if you'd need to do this from a live session or not. I use a 3rd party boot/partition manager so am not real familiar.

---

### Post by PopsTheSailor on 2015-03-06
As usual, I haven't given enough information. I'm running Ubuntu 14.04 MATE and got here by way of upgrades. I've been using this particular install for over a year. I have lots of apps and other configurations installed. A week or so ago, I got the standard update manager request and installed the updates. Shortly (note, not immediately which is odd) after that, I lost my MATE UI. My background comes up but no icons on the desktop, no menus, etc.. Just a nice full screen with a pretty picture. 

I want to fully uninstall MATE and then reinstall it back over my configuration in hopes that that will correct my issue. So you see I can't just smash the partition and start over because I would lose a years worth of tweaking.

---

### Post by yancek on 2015-03-06
The link below explains how to do it on 14.04.  The page also has a link on how to install it.  Never done this myself so...?

[http://sourcedigit.com/12228-uninstall-remove-mate-desktop-ubuntu-14-04-lts/](http://sourcedigit.com/12228-uninstall-remove-mate-desktop-ubuntu-14-04-lts/)

Here's another link.

[http://linuxg.net/how-to-properly-installremove-mate-1-8-onfrom-ubuntu-14-04-trusty-tahr/](http://linuxg.net/how-to-properly-installremove-mate-1-8-onfrom-ubuntu-14-04-trusty-tahr/)

---

### Post by grahammechanical on 2015-03-06
It seems to me that your question should be: How do I reinstall Ubuntu Mate wihtout over-writing the /home folder and loosing all my configuration files and documents. You do that by

1) Using a live session to backup those important documents
2) Install using the Something Else option. You will need to tell the Installer which partition to install Ubuntu Mate into.

a) At the partioning screen select the partition and click Change
b) Select the file system type from the Use As drop down menu. Choose Ext4
c) Do Not tick the box Format the Partition. I repeat - Do not tick the box format the Partition.
d) Select the mount point as /
e) click OK

That will re-install whatever flavour of Ubuntu we are using without formating the partition and so preserve what is it in the /home folder. You will need to re-install applications that are not part of the default set of applications. But they will detect their configuration folders in /home.

An alternative is to try to fix the problem. I would try

Firstly - selecting Recovery mode at the Grub boot menu and at the Recovery menu I would then select Resume. That should get us to a desktop using a fall back open source video driver. Then I would open additional drivers and experiment with video drivers.

Secondly, if this was Ubuntu where I was getting the desktop wallpaper without the launcher or the top panel, I would right click the wallpaper and select Change Desktop Background. That will open system Settings at the Apperance utility. Now that I was in System Settings I would then go to Additional Drivers and experiement with video drivers. I have no idea if this will work with Ubuntu Mate.

EDIT: In Ubuntu Mate right click the wallpaper and select Open in Terminal and run

```
software-properties-gtk
```

That will open Software and Updates. From there we can use the Additional Drivers tab to change video driver.

Regards.

---

### Post by deadflowr on 2015-03-06
> I'm running Ubuntu 14.04 MATE and got here by way of upgrades.

What does this mean?

How did you get mate on this system to begin with?

---

### Post by PopsTheSailor on 2015-03-06
[ 						 							]("http://ubuntuforums.org/member.php?u=1087323")grahammechanical,
I've already tired right clicking on the desktop. I get absolutely nothing. I'm am not yet ready to throw in the towell and do a reinstall. I have Wine installed with a bunch of stuff. I also have virtual box installed with 2 different instances configured not to mention tons of other stuff. I'll try booting to recovery mode and see what I can get. Also, I think when I boot, I can hit control-alt-F2 or something and get to a command prompt where I can log in. I was wondering if there are any commands to reset the UI or UI config tools I could load and try and reset back to the default settings.

Deadflowr,
you have 2 options that I know of. First, you can go to Ubuntu's official download page and they now have a live CD that comes with the MATE desktop. That would have to be a fresh install. Option 2, if you are already running Ubuntu 14.04 with Unity, you can go to this link. It has instructions on how to install MATE on a current Unity install.

[http://sourcedigit.com/12224-install-mate-desktop-ubuntu-14-04-lts/](http://sourcedigit.com/12224-install-mate-desktop-ubuntu-14-04-lts/)

Hope that's helpful!

---

### Post by buzzingrobot on 2015-03-07
> **PopsTheSailor said:**
> I installed Ubuntu MATE 14.04 using the Install CD that was prebuilt with MATE. I need to completely uninstall the MATE UI. How do I do that?

I'm not at all sure you can do that cleanly. MATE is the only desktop environment in Ubuntu MATE.  Any successful attempt to remove MATE will leave you with a system that boots to a command prompt, if you reconfigure it correctly. If you're uncomfortable with that prospect, and you want to reinstall MATE anyway, it's likely going to be simpler, quicker and safer to reinstall from scratch.

MATE's dependency chain would, I suspect, also result in the removal of a number of core components in the Ubuntu base.

---

### Post by PopsTheSailor on 2015-03-07
I have 2 different installs of Ubuntu. It turns out the other one (the one working) is the one I installed with the MATE live CD. The one I'm having trouble with is one that I installed MATE on top of Unity. It ran fine for a year. 

So I can get my UI back if i boot and then go into recovery mode and resume as grahammechanical suggested. I opened additional drivers but none appear. How do I set my graphics to the same state that is used when I resume? This seems like it would fix my problem.

Oh and one more thing. I created a new user and the UI comes up just fine without having to go through recovery mode. So it's something with my user configuration.

---

### Post by buzzingrobot on 2015-03-07
If an Intel card is active, Additional Drivers will show no available proprietary drivers. Intel open sources that driver and it is installed and used automatically.

If an Nvidia or AMD card is active and if a proprietary driver for the card is available in the repos and if that driver is compatible with your kernel version and your version of Ubuntu, then it should be offered for installation.

If things work OK with that new user, why not try deleting and recreating the "bad" user and see what happens? Copy that user's home folder off somewhere safe, delete and recreate that user, then see if things are OK when you log in as that recreated user.  If they are, copy the contents of that backed-up home folder back in place, log out and log in again.  If the problem reappears, it has to be something in one of the those files.

---

