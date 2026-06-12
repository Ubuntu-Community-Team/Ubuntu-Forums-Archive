---
title: "Nothing loads after login - blank orange screen"
date: 2007-09-06
forum: Desktop Environments
---

### Post by mhoydis on 2007-09-06
Hiya.  I uninstalled my ATI driver and reinstalled it (long story).
Now, when I login, I get the blank orange screen as if its about to load, but nothing happens.  No menu bar, no nothing.  How can I troubleshoot this?

---

### Post by swisscow on 2007-09-06
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Hit CTRL ALT F1 - this will bring up a command line. Login (if necessary). Type the above in. This will give you the opportunity to set the settings correctly. For the video card Vesa should work for it if you're stuck for choice.

---

### Post by mhoydis on 2007-09-06
fglrx is the right driver.  I've already done this and it hasn't changed the situation.
I think there's some kind of script it isn't trying to run, but I don't know what it is.  I've searched /var/log/messages and have found nothing useful.  other logs also.  I'm totally stumped.
It isn't "crashing" because I can ctrl+alt+backspace, it'll flash around, and i'll be back at the login window again.

Does anybody know the sequence of startup scripts this goes through?  Or what could have possibly have changed with just the removal/reinstallation of the ATI drivers from the package manger?

---

### Post by swisscow on 2007-09-06
Ok, the fglrx driver is the right one but the vesa will get you going.

Sometimes the fglrx driver is a pain in the rear to get going - I use these instructions which works for me:

```
http://ubuntuforums.org/showthread.php?t=542848
```

---

### Post by mhoydis on 2007-09-06
There may be a misunderstanding here.  X  is starting.  I'm getting a display.  The gnome menubar thingie isn't coming up.  I'm getting no window manager.  I see the gnome-stylized mouse cursor, which I can move, on the default orange background color.

it's like X is starting but not calling to load up anything else.  it's like a post-gdm thing.

---

### Post by swisscow on 2007-09-06
Ah sorry, I got the wrong end of the stick

This command (from google) should restart the gdm 

```
/etc/init.d/gdm restart
```

If that doesn't work I don't know.

Sorry for not getting it right. Good luck

---

### Post by mhoydis on 2007-09-06
gdm is functioning.  it does not need to be restarted.  the problem is AFTER the gdm login.

---

### Post by mhoydis on 2007-09-06
this is what is happening to me:
[https://answers.launchpad.net/ubuntu/+source/xen-source-2.6.17/+question/2610](https://answers.launchpad.net/ubuntu/+source/xen-source-2.6.17/+question/2610)

only when I press ctrl+c, it does not resume loading.

---

### Post by swisscow on 2007-09-06
Well sometimes restarting (like rebooting windows ) can help. I suggest looking round google, there are a number of responses there but from what I've read it varies according to the video card you have which you haven't mentioned.

---

### Post by mhoydis on 2007-09-06
this...  [http://ubuntuforums.org/showthread.php?t=413975](http://ubuntuforums.org/showthread.php?t=413975)
is what's happening.  Lordy loo.

---

### Post by mhoydis on 2007-09-06
auugg no.  that's almost what's happening, only my hang happens after the login, not before the login.
there's obviously something trying to run that' failing and I cannot see what it is.  If anybodu knew what startup scripts I should look at, I could fix this.  I just don't know the path of scripts this follows...

---

### Post by mhoydis on 2007-09-06
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg429792.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg429792.html)

This is what I did.  I installed and removed the nvidia drivers.  I wish I knew what this broke :(

---

### Post by mhoydis on 2007-09-10
Figured this out.  The nvidia driver package had removed Gnome Core Components package when it was uninstalled.

---

### Post by marx2k on 2007-09-13
So did you reinstall it? Did this fix the issue? I am having the same exact issue here.

---

### Post by marx2k on 2007-09-13
Works like a charm :) Thanks for the info! This saved me from having to reinstall Gnome and KDE! (And VMWare, and NetBeans, And etc etc etc)

---

### Post by CathS on 2007-09-14
I have the same problem.   I've just installed Ubuntu as a dual boot on an Toshiba Satellite P30.  It worked like a charm after installation until I updated the driver for my usb wireless device.  Then, after rebooting the machine, I log in, get the splash screen, open into the main ubuntu window, then it crashes.

Depending whether I boot into gnome or gnome safe mode I either see the two menu bars, but blank, or the menu bars with text, but inactive.  My mouse works, but I can't select anything.  The hot keys don't work.

I've tried a complete reinstallation with no success.  I'm new to Linux and don't have a clue how to proceed.  Can anyone help?

(btw, my video drivers - Radeon Mobility - are apparently compatible with Ubuntu, so it's not that - I've tried updating them anyway with no success).

---

### Post by CathS on 2007-09-16
Never mind.  I switched to Kubuntu instead and it works.  Must be something gnome related.

---

### Post by silanea on 2007-09-19
I had the same problem with a fresh install of Ubuntu 7.04 Desktop on an FSC Lifebook E7110 (ATI Mobility Radeon 7500). It seems to occur randomly. Reconfiguring X to use something other than the vesa driver (ati in my case) solved it for me.

---

