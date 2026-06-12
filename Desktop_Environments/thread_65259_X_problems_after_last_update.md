---
title: "X problems after last update"
date: 2005-09-13
forum: Desktop Environments
---

### Post by spacemonkey on 2005-09-13
Not sure if this is the right place for this, but after the big update the other day, after a reboot of my machine, X will no longer start.  It was working perfectly before, but now, the nvidia splash screen shows up, then it crashes to the terminal.  When I run startx after logging into the terminal, the same thing happens.  It gives a few error messages, but I can't remember them all right now.  If someone could tell me how to put the startx output into a file from the terminal, then I could get the error messages.  Also, I'll post my xorg.conf file.  Any help would be greatly appreciated, because I use hoary as my main OS, and having to run windows instead is no fun at all.

---

### Post by agm642 on 2005-09-13
I'm no expert myself, but in order to get its output in a file, try startx > filename.

---

### Post by rafakl on 2005-09-13
Try reinstalling the gnome desktop:

sudo apt-get --reinstall install gnome-desktop  :razz:

---

### Post by spacemonkey on 2005-09-13
I tried reinstalling the xorg, and a few other things, but got nothing.  Then I tried the nv driver instead of nvidia, and it worked, which seemed strange to me because I assumed that if I got the nvidia splash screen, then the driver was functioning, but anyways, I downloaded the latest nvidia driver (I was using 7667, now I'm using 7676), installed it, and everything is working fine.

---

### Post by LokeDK on 2005-09-13
I had problems too..
The logs says
Could not init font path element unix/:7100, removing from list!

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Fatal server error:
Caught signal 11.  Server aborting


Please consult the The X.Org Foundation support 
	 at [http://wiki.X.Org](http://wiki.X.Org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

But it helped with reinstalling the nvidia driver (was- and am  using the latest)
I hope it's not gonna happen again.

---

### Post by paul cooke on 2005-09-13
[QUOTE=LokeDK]I had problems too..
The logs says
Could not init font path element unix/:7100, removing from list!

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Fatal server error:
Caught signal 11.  Server aborting


Please consult the The X.Org Foundation support 
	 at [http://wiki.X.Org](http://wiki.X.Org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

But it helped with reinstalling the nvidia driver (was- and am  using the latest)
I hope it's not gonna happen again.[/QUOTE]
 I've got X, but nvidia's gone... tried 

sudo dpkg-reconfigure xserver-xorg
followed by 
sudo nvidia-glx-config enable

 and then restarting X, but no joy... no nvidia splash and the 3D has gone to pot

now where?

---

### Post by jameswilhelm on 2005-09-13
Had (perhaps) same problem here.

Did the HUGE update tonight. Everything worked fine afterwards - phew!!! Until I tried to run Bzflag, Doom3demo and Nexuiz. The nvidia screen did also not appear during bootup or when doing a 'New login'.

Bzflag gave an error about Glx extension missing when run from commandline. I then reinstalled:
 - nvidia-glx
 - nvidia-kernel-common

Reboot - No luck.

Then changed the "nv" driver to "nvidia" in /etc/X11/xorg.conf. Rebooted and it worked!

I don't think the driver reinstall solved anything. It looks like xorg.conf got overwritten during the update. Will keep a backup from now on!

---

### Post by paul cooke on 2005-09-13
[QUOTE=jameswilhelm]Had (perhaps) same problem here.

Did the HUGE update tonight. Everything worked fine afterwards - phew!!! Until I tried to run Bzflag, Doom3demo and Nexuiz. The nvidia screen did also not appear during bootup or when doing a 'New login'.

Bzflag gave an error about Glx extension missing when run from commandline. I then reinstalled:
 - nvidia-glx
 - nvidia-kernel-common

Reboot - No luck.

Then changed the "nv" driver to "nvidia" in /etc/X11/xorg.conf. Rebooted and it worked!

I don't think the driver reinstall solved anything. It looks like xorg.conf got overwritten during the update. Will keep a backup from now on![/QUOTE]


did the re-installation of the nvidia-glx and kernel stuff, restarted X, no joy, checked the xorg.conf, yes, the driver was set to nvidia... weird...

Now I had noticed that during the X restart, and during the normal boot sequence, I'd had a lot of blank screens and "No signal" come up on my monitor... I was beginning to suspect  graphics hardware... 

got my known good live distro, that I know supports nvidia in 3D mode, (elive, try it, you'll find enlightenment e17 is fantastic)... it gave me some trouble at the start, I had to operate the boot menu blind as I had a blank screen and "No signal" come up ... got it to carry on the boot sequence... and lo and behold, a nice nvidia logo... rebooted with the live disk removed... and well, here I am with working nvidia... and no blank screens during the boot either... whereas a few minutes ago, it refused to play... I strongly suspect that something on my graphics card required a good "kick" to get it back to where it should be...

---

### Post by jameswilhelm on 2005-09-13
Interesting. Perhaps there are settings on the graphics card that can get messed up? No idea. At least it is working now.

One of the many things I would still like to do is to try other desktop environments / windows managers. Have so far only used a bit of KDE and mostly Gnome. Will give elive a go. Thanks.

---

### Post by factotum218 on 2005-09-13
Same problem here, started mmmmm...friday or saturday maybe after running an update. Haven't done anything but switch from "nvidia" to "nv" in my xorg since then, been to busy to troubleshoot anything so far this week. Good to see I'm not the only one with this problem. Hasn't affected anything since i dont do much of any gaming, but I'll look into what available for update.

Whoa, lots of upgrades here, had to use the -f option for some reason maybe because of firefox, but hopefully this will help.

---

### Post by linkunderscore on 2005-09-14
[QUOTE=spacemonkey]I tried reinstalling the xorg, and a few other things, but got nothing.  Then I tried the nv driver instead of nvidia, and it worked, which seemed strange to me because I assumed that if I got the nvidia splash screen, then the driver was functioning, but anyways, I downloaded the latest nvidia driver (I was using 7667, now I'm using 7676), installed it, and everything is working fine.[/QUOTE]


can u explain what you did because I am having the exact same problem. I am a novice at linux and I really don't know what to do.

---

### Post by rjstevens3 on 2005-09-14
i'm having the same problem. my /var/log/Xorg.0.log ends with failed load of /usr/X11R6/lib/modules/extensions/libGLcore.a

i tried reinstalling gnome-desktop with no luck. any ideas...

---

### Post by dysprosium on 2005-09-14
Same problem here.  Just updated.  Anyway to undo the updates?  That's all I can think of.

---

### Post by Luke Redpath on 2005-09-14
Also had this problem after my first reboot after the big update. I seem to remember there being some kernel updates and I also remember the Nvidia installer saying that the drivers needed to be reinstalled if the kernel was updated, so thats what I did. Booted into recovery mode, loaded up elinks and downloaded the latest Nvidia drivers. Removed the existing kernel module ("sudo rmmod nvidia") then run the installer. All is well.

---

### Post by linkunderscore on 2005-09-14
[QUOTE=Luke Redpath]Also had this problem after my first reboot after the big update. I seem to remember there being some kernel updates and I also remember the Nvidia installer saying that the drivers needed to be reinstalled if the kernel was updated, so thats what I did. Booted into recovery mode, loaded up elinks and downloaded the latest Nvidia drivers. Removed the existing kernel module ("sudo rmmod nvidia") then run the installer. All is well.[/QUOTE]


This worked for me. I just changed the xorg.conf to "nv". Booted back into gnome and followed the wonderful instructions in the How To: Latest Nvidia drivers thread. It removes the old drivers for you and re-installs again. Works flawlessly.

---

### Post by sorry_name_taken_already2 on 2005-09-15
[QUOTE=rafakl]Try reinstalling the gnome desktop:

sudo apt-get --reinstall install gnome-desktop  :razz:[/QUOTE]

Thanks I tried that! [COLOR=Red]I thought Linux/ubuntu was stable and safe[/COLOR]. A little touchy and little tweaking admitedly! It is like driving an Alfa or any Italian automobile. It's expected that you have to get yours hands dirty to keep it running lean and fast . I was prepared to learn but the rules keep changing! [COLOR=Red]I did the recent update 30.1mb and all! I noticed it was to do with fonts and lib files.[/COLOR] Anyways, I trusted snaptypic (however, you spell it) and to my horror after restarting it this morning. _The colours of my GDM was reduced to 16 colours depth_. I am afraid to hack with the xconfig.org being a noob!

What the?! The repository just assumes that I want to update to the breezy development release?! Im all so confused after reading in forums that fonts are in a different folders and dynamic links here and there... I just had a sweet set up for a simpleton like myself. I was happy to surf the net, use Gaim, K3B and even connects to the windows domain without much effort!

I also noticed that like the previous post that the update updated my kernel! When i reboot I get this message "[COLOR=Red]ACPI unable to locate RSDP[/COLOR]"!
I never had that prob before and my bios/motherboard supports ACPI!

Cries ... I want my computer back or back to Windoze for me! ](*,) 
Someone email me at [email]curious_@hotmail.com[/email] asap ... I am tempted to put XP back on!

PIII 650eb
128MB RAM
13GB HDD
Generic MB w 6160 MSI pro chipset
Savage AGP

---

### Post by jjennings089 on 2005-09-15
[QUOTE=spacemonkey]Not sure if this is the right place for this, but after the big update the other day, after a reboot of my machine, X will no longer start.  It was working perfectly before, but now, the nvidia splash screen shows up, then it crashes to the terminal.  When I run startx after logging into the terminal, the same thing happens.  It gives a few error messages, but I can't remember them all right now.  If someone could tell me how to put the startx output into a file from the terminal, then I could get the error messages.  Also, I'll post my xorg.conf file.  Any help would be greatly appreciated, because I use hoary as my main OS, and having to run windows instead is no fun at all.[/QUOTE]

Your xorg.conf file says you still have the Load "dri" & "GLcore" Module.  Comment out those lines.  See [http://ubuntuforums.org/showthread.php?t=52924&highlight=Nvidia+7676](http://ubuntuforums.org/showthread.php?t=52924&highlight=Nvidia+7676)

---

### Post by jjennings089 on 2005-09-15
[QUOTE=sorry_name_taken_already2]Thanks I tried that! [COLOR=Red]I thought Linux/ubuntu was stable and safe[/COLOR]. A little touchy and little tweaking admitedly! It is like driving an Alfa or any Italian automobile. It's expected that you have to get yours hands dirty to keep it running lean and fast . I was prepared to learn but the rules keep changing! [COLOR=Red]I did the recent update 30.1mb and all! I noticed it was to do with fonts and lib files.[/COLOR] Anyways, I trusted snaptypic (however, you spell it) and to my horror after restarting it this morning. _The colours of my GDM was reduced to 16 colours depth_. I am afraid to hack with the xconfig.org being a noob!

What the?! The repository just assumes that I want to update to the breezy development release?! Im all so confused after reading in forums that fonts are in a different folders and dynamic links here and there... I just had a sweet set up for a simpleton like myself. I was happy to surf the net, use Gaim, K3B and even connects to the windows domain without much effort!

I also noticed that like the previous post that the update updated my kernel! When i reboot I get this message "[COLOR=Red]ACPI unable to locate RSDP[/COLOR]"!
I never had that prob before and my bios/motherboard supports ACPI!

Cries ... I want my computer back or back to Windoze for me! ](*,) 
Someone email me at [email]curious_@hotmail.com[/email] asap ... I am tempted to put XP back on!

PIII 650eb
128MB RAM
13GB HDD
Generic MB w 6160 MSI pro chipset
Savage AGP[/QUOTE]

Since this is a Savage Card and we have no xorg.conf file; I'm just going to make a wild stab at this one.

ctl-alt-f1 (so as to get to the command line)
login with your username and password
sudo /etc/init.d/gdm stop (or "kdm stop" if you use KDE)
sudo cp /etc/X11/xorg.conf /etc/X11/backup-xorg.conf (backing up your xorg.conf file)
cd /etc/X11/
sudo dexconf (Debian X Configuration tool)
sudo /etc/init.d/gdm start (or "kdm start" if you use KDE)

---

### Post by rossman on 2005-09-16
I had the same problem.  Restoring the pre-update xorg.conf fixed it for me:

cd /etc/X11
sudo cp xorg.conf-backup xorg.conf

HTH
Ross

---

