---
title: "ATI drivers boot to shell"
date: 2007-10-25
forum: Desktop Environments
---

### Post by dalamar666 on 2007-10-25
I know that the problem I am having is somewhere in my drivers.  I was trying to update my drivers to the 8.40.3 from the 8.36 I was using in an attempt to get some video games to work better.  

My machine will boot when it gets to the kubuntu loading screen the line goes all the way across and then I get kicked out of there and loads to a command prompt.  I have tried running sudo apt-get update and sudo apt-get -f install and dpkg configure(I think) xserver.xorg to try and resetup things with the xserver and no luck.  It is also telling me that there is not a backup image to boot to.  I was running through some commands I found in a forum where I would install the driver I downloaded and then I installed the .deb packages for it and recompiled the kernel.  Rebooted all good.  Then I edited the xserver config file thing and replaced the flgrx in the device line with ati rebooted and that is when the machine took a shat.  

System specs

Kubuntu 7.10 loader with gnome availablity.  AMD 64 processor 2 gig processor 3200+ Orleans.  Video card is the radeon X1650.  

Live version boots and works.  No terminal etc but still boots.  Is there a file I can copy from the cd to fix everything?

I have also looked into doing a "repair install" like from windows or a "last known good" to remove the driver and adjust the settings and no good.  I REALLY love ubuntu and am a recent windows convert.  Busting the os within a week of install is a new record for me lol.  Any help will be greatly appriciated.  I can copy all my files and stuff like that and reinstall but yeah after windows doing OSRI's while is a fact of life and something I am used to, I would rather fix the problem with the current install.  There has to be a way to fix this without that.

---

