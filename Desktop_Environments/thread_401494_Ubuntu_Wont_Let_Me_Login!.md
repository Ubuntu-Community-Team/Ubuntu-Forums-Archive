---
title: "Ubuntu Wont Let Me Login!"
date: 2007-04-04
forum: Desktop Environments
---

### Post by justincormier on 2007-04-04
So i've been using this OS for about 13 hours now... so this might get complicated..

i installed Ubuntu, was having a blast.. quite possibly the most fun ive ever had on an operating system.. I run my updater and it has me install about 160 updates.  It downloads and installs, but says some have errors.  I figure its no big deal.  I reboot and get to my login.. type my username and password and the screen goes black and then im right back at the login screen...  IT DOES NOT SAY INCORRECT USERNAME/PASSWORD... it just brings me back.. Ubuntu doesnt seem to load after login.  

some other odd problems.
- im pretty sure my graphics card is not properly configured - ati radeon 7500
- im also pretty sure the internet is REAL slow.. while downloading updates i was travelin at 13k.


other than that.. I just need some help bad.

thanks for your time in advance.. remember go slow.. i feel like a 7 yr old right now...

Jusitn

---

### Post by borobudur on 2007-04-04
Can you get to the terminal session at the login screen? if yes you should go there and do this:

[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Graphics_Driver_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Graphics_Driver_.28ATI.29)

---

### Post by Zwalther on 2007-04-04
Hi Justin,

This is kind of a hard problem, because I have no idea of what went wrong during your update. But you can try the following to get a bit further.

When you log in (before you press enter after typing in your password) try to select a different session. If you can't find something labeled session on your login screen, press F10 to get a menu.

The "Failsafe terminal" session should always work. From there you can do sudo synaptic. This will start up the package manager. If you press "Custom filters" in the lower left and then select "Broken" if the left panel, you can find the packages that didn't install correctly. Perhaps you can try to reinstall or delete those packages.

Good luck and if you can get any more information just post it again.

---

### Post by justincormier on 2007-04-04
ok i was trying all sorts of those things...

and i got to a disk check screen that said hda6 was not properly mounted..

then somehting about exe3 died ...... fail


i couldnt read it cause it flashed too quick.... any ideas...


--EDIT--

i used the command run (ctrl + alt + f2) and was able to login... switched back to my gui and then was asked to login there.. after doin so i recieved...

"GDM could not write your authorization file.  this could mean you are out of diskspace or that our home directory could not be opened for writing.  In any case, it is not possible to log in.  Please contact your system administrator"

---

### Post by Zwalther on 2007-04-04
So, are you out of diskspace? You can check by loggin in to the terminal (ctrl + alt + f2) and do "df -h" there.

If there is a problem with your disk partitions, it might be wise to reinstall. It's not easy to fix if you don't have linux/unix experience.

---

### Post by justincormier on 2007-04-04
yeah i decided to reinstall.. but ive noticed a few other recent posts on the board stating similiar problems...  ironically, what took me 6 hours to figure out yesterday (install, partition, mp3, installing apps) only took me 20 mins to do today..

hahah oh wel.. i still like it better than windows and any of the mac crap.

---

### Post by rshawgo on 2007-04-04
I had a similar problem after letting the package manager install updates this morning.  Eventually tried reinstalling the NVIDIA video drivers and all was fine.  Not sure if that will solve your issues, but it may be worth a try, assuming it is not too late.  

Best of luck.
Ryan

> **justincormier said:**
> So i've been using this OS for about 13 hours now... so this might get complicated..

i installed Ubuntu, was having a blast.. quite possibly the most fun ive ever had on an operating system.. I run my updater and it has me install about 160 updates.  It downloads and installs, but says some have errors.  I figure its no big deal.  I reboot and get to my login.. type my username and password and the screen goes black and then im right back at the login screen...  IT DOES NOT SAY INCORRECT USERNAME/PASSWORD... it just brings me back.. Ubuntu doesnt seem to load after login.  

some other odd problems.
- im pretty sure my graphics card is not properly configured - ati radeon 7500
- im also pretty sure the internet is REAL slow.. while downloading updates i was travelin at 13k.


other than that.. I just need some help bad.

thanks for your time in advance.. remember go slow.. i feel like a 7 yr old right now...

Jusitn

---

### Post by +Kardboard+ on 2007-04-06
Wonderful, was having the same issue and reinstalled my NVIDIA drivers and the problem is now gone!  Seems to be related to a kernel update from Synaptic after all!

---

