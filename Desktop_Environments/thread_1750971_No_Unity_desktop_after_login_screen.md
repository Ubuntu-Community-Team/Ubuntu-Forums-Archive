---
title: "No Unity desktop after login screen"
date: 2011-05-06
forum: Desktop Environments
---

### Post by Siegemos on 2011-05-06
Hi all,

First off apologies if this issues has already been raised, I found some similar issues using the search but none of them have helped.

I have recently downloaded and installed Ubuntu 11.04 desktop. I'd like to be able to dual boot into Windows or Linux on my PC so I've installed in on an ext4 partition on a separate drive from Windows.

The installation process ran smoothly and the dual boot functionality works as planned. The problem I'm having is that after logging in, the login window disappears (as does the options bar at the bottom of the screen), and then nothing else appears, just the mouse cursor (sometimes the loading icon, sometimes not) and an empty background image, no icons, no menus. It doesn't matter how long I leave it for, nothing ever happens from this point on. 

I am technical, however, unfortunately ,I'm very new to Linux (something I'd like to remedy) so I'm a bit stuck with what to try next. Any pointers would be appreciated.

Thanks.

---

### Post by An Sanct on 2011-05-06
The Unity tab is located to the left of your screen, maybe its hidden or something.

If you want, you can also choose the classic desktop in the login screen (in the bottom). 

Try classic first, update to the latest update and then try Unity again.

---

### Post by Siegemos on 2011-05-06
Hi, thanks for the reply. 

Ubuntu classic doesn't seem to work either unfortunately. The process is this:

I type my login details, everything disappears, the Ubuntu intro sound plays, cursor turns to loading, then nothing else happens.

Ubuntu (Safe mode) does work however, I get straight in. I'm guessing that safe mode loads the OS without some drivers so I guess now my question becomes: How do I find out what the problem with the 'non safe-modes' is?

Thanks.

---

### Post by An Sanct on 2011-05-06
My bet would be, go to the "rescue console" and run
```
sudo apt-get update
sudo apt-get upgrade
```
or alternatively, run updates in safe mode.

Maybe there are some updates, that need to be installed for your hardware to work okay with Natty.

---

### Post by ilanrab on 2011-06-26
> **Siegemos said:**
> Hi all,

First off apologies if this issues has already been raised, I found some similar issues using the search but none of them have helped.

I have recently downloaded and installed Ubuntu 11.04 desktop. I'd like to be able to dual boot into Windows or Linux on my PC so I've installed in on an ext4 partition on a separate drive from Windows.

The installation process ran smoothly and the dual boot functionality works as planned. The problem I'm having is that after logging in, the login window disappears (as does the options bar at the bottom of the screen), and then nothing else appears, just the mouse cursor (sometimes the loading icon, sometimes not) and an empty background image, no icons, no menus. It doesn't matter how long I leave it for, nothing ever happens from this point on. 

I am technical, however, unfortunately ,I'm very new to Linux (something I'd like to remedy) so I'm a bit stuck with what to try next. Any pointers would be appreciated.

Thanks.

Same issues. No solution so far.
PuppyLinux works fine on this laptop.

---

### Post by ilanrab on 2011-06-26
> **ilanrab said:**
> Same issues. No solution so far.
PuppyLinux works fine on this laptop.

Found solution to this 11.04 upgrade from 10.10:

1. Boot up into the Linux degraded mode and wait a few moments.
2. When presented with a dialog list, select the "low graphics" mode.
3. Once the desktop is up, select tools>administration>LoginScreen
4. Enter your authentication key to unlock the dialog.
5. Choose whatever login options you want and near the bottom of the dialog select the "Ubuntu Classic" logon.
6. Reboot.

---

### Post by jvgeli on 2011-07-08
Could be a graphics issue. What is your GPU card? I'm guessing ATI?

---

### Post by jinliew on 2011-08-03
Hi,

I have the same issue I think, which first started happening with 11.04.  No problems with 10.04 which I had previously.  I upgraded from 10.04 to 10.10 and then straight to 11.04.

Symptoms / Issue:
* Unable to log in to graphical console - either freezes just after login with the wait cursor OR loads desktop wallpaper and cannot get any further.  Mouse is active, but unity does not start.

Setup:
Ubuntu version: 11.04
Graphics: Nvidia
Graphics driver: proprietary 280.xx from x-swat PPA

Previously I've gotten it to work by uninstalling and reinstalling combinations of the graphics driver and ubuntu desktop, but now the fix doesn't work any more.

Any help would be greatly appreciated.  I used to like Ubuntu, but I'm starting to run out of patience with this issue =(

Thanks!

---

### Post by Krytarik on 2011-08-03
@jinliew: Try the nvidia-173 driver instead. Therefore, log in to "Ubuntu Classic (No effects)" and install/activate it through "System -> Administration -> Additional Drivers".

Greetings.

---

### Post by jinliew on 2011-08-04
Hi after many uninstallations and reinstallations of my graphics drivers, unity and ubuntu desktop, I got it working with the 173 drivers.

However, recent 3D games do not seem to work with these drivers, so this isn't a good enough workaround for me.  Switched back to the current drivers and unity hangs.


Is there a compatibility problem between unity and recent Nvidia drivers??


Sorry but my patience is hanging by a thread.  I'm about to either downgrade back to 10.04 or switch to another distro =(

---

### Post by jinliew on 2011-08-04
oh and I've been using Ubuntu for a couple of years now.  It would be a real shame to switch, but I'm spending more time fixing my computer than I am using it productively...

---

