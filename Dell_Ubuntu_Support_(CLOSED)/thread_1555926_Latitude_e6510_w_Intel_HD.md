---
title: "Latitude e6510 w/ Intel HD"
date: 2010-08-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by acroporas on 2010-08-18
Can anyone help me install ubuntu on a Dell Latitude e6510 with Intel HD Graphics. The live cd boots (can hear the welcome jingle) but the screen is blank.

---

### Post by mörgæs on 2010-08-19
I assume that you are using 10.04. How does the machine behave with another version? 

[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

---

### Post by klsitton on 2010-08-20
I also have a new e6510.  10.04.1 doesn't have a usable driver for the laptop display adapter.  I got around this by using an external monitor plugged into the VGA port.  I was then able to install Lucid, then access the internet to get the third party / proprietary drivers used with this video adapter hardware.  The NVIDIA driver works well with the integrated display after installed.

---

### Post by acroporas on 2010-08-20
> **klsitton said:**
> I also have a new e6510.  10.04.1 doesn't have a usable driver for the laptop display adapter.  I got around this by using an external monitor plugged into the VGA port.  I was then able to install Lucid, then access the internet to get the third party / proprietary drivers used with this video adapter hardware.  The NVIDIA driver works well with the integrated display after installed.

I think that it is VERY unlikely that an NVIDIA driver would work well on an Intel graphics card??  Additionally, external monitor plugged into the VGA port has the same black screen problem...

---

### Post by acroporas on 2010-08-20
> **mörgæs said:**
> I assume that you are using 10.04. How does the machine behave with another version? 

[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)



10.10 - No screen output.
10.04 - No screen output.
9.10 - Crashes IMMEDIATELY
9.04 - Neither the wired or wireless network works.  Compiz does not work.

---

### Post by mörgæs on 2010-08-21
There seems to be a lot of trouble with these machines. Maybe this thread will help:

[http://ubuntuforums.org/showthread.php?t=1521522](http://ubuntuforums.org/showthread.php?t=1521522)

---

### Post by acroporas on 2010-08-24
I have made progress.  What I have learned.  

I needed to add "i915.modeset=0 xforcevesa" to the boot options.  After doing that I was able to boot the live CD and install.  Then I added the same to the boot options in grub and I was able to boot the computer.

After installation I noticed 2 things that did not work.  Wireless, and compiz.

My wireless chip is a Broadcom 4353 (Dell 1520).  Even after installing the closed source drivers, wireless still did not work. I selected the "Unsupported Updates" option in software sources, and then installed "linux-backports-modules-wireless-lucid-generic"  which fixed the wireless issues.

Now all that remains is compiz....

---

### Post by semmypurewal on 2010-08-24
acroporas:

Desktop effects probably don't work because you're still using the vesa driver.

I managed to get the intel driver to work, but only by using the backported maverick kernel.  Of course, then I had some trouble getting the wireless to work, but it all appears to be working now.

I just wrote up my solution in [this thread]("http://ubuntuforums.org/showthread.php?t=1509957&page=2"):

[http://ubuntuforums.org/showthread.php?t=1509957&page=2](http://ubuntuforums.org/showthread.php?t=1509957&page=2)


I hope it helps!

---

### Post by acroporas on 2010-08-24
I followed the first part of your instructions.  Up to editing xorg.conf.  But on my computer /etc/xorg.conf does not exist....So I couldn't edit it...I tried creating a file at /etc/xorg.conf with the one line in it.  Did not help.

At that point booting without the kernel parameters did not work, nor did wireless.  So I tried to undo the changes to get back to where i was before, which was unsuccessful.  I was able to remove the maverick kernel, but that did not fix wireless...

I think it's time to re-install...and try again.  


> **semmypurewal said:**
> acroporas:

Desktop effects probably don't work because you're still using the vesa driver.

I managed to get the intel driver to work, but only by using the backported maverick kernel.  Of course, then I had some trouble getting the wireless to work, but it all appears to be working now.

I just wrote up my solution in [this thread]("http://ubuntuforums.org/showthread.php?t=1509957&page=2"):

[http://ubuntuforums.org/showthread.php?t=1509957&page=2](http://ubuntuforums.org/showthread.php?t=1509957&page=2)


I hope it helps!

---

### Post by semmypurewal on 2010-08-24
acroporas:

Oops, sorry.  That was a typo.  The file should be /etc/X11/xorg.conf not /etc/xorg.conf

Sorry for the confusion!  I fixed it in the original post.

You should probably back up your xorg.conf file before you edit it (in case you make a mistake).  To do that:

```

cd /etc/X11
sudo cp xorg.conf xorg.conf.BACKUP
sudo nano xorg.conf

```

---

### Post by orange_roughy on 2010-08-24
wifi on this system is driving me nuts. I tried semmypurewal's suggestions. If it matters, I'm on 32-bit Karmic, not 64-bit Lucid.

I've got the Broadcom 4353 (Dell 1520) wifi card. Network applet shows all SSIDs of the networks, but I cannot connect to any of them... even if there's no WEP/WPA encryption (e.g., at Starbucks).

help!

---

### Post by acroporas on 2010-08-24
semmypurewal, 

Your instructions still are not quite working for me (after a fresh install)  I went though all the steps and the screen is still black at boot.

However I did discover that plugging in an external LCD brings the built in display to life.  I can then unplug the external monitor, the built in display continues to work, and Compiz does work.

---

### Post by mörgæs on 2010-08-24
> **orange_roughy said:**
> wifi on this system is driving me nuts. I tried semmypurewal's suggestions. If it matters, I'm on 32-bit Karmic, not 64-bit Lucid.

I've got the Broadcom 4353 (Dell 1520) wifi card. Network applet shows all SSIDs of the networks, but I cannot connect to any of them... even if there's no WEP/WPA encryption (e.g., at Starbucks).

help!

First step: Have you installed all updates using wired internet access?

---

### Post by semmypurewal on 2010-08-24
acroporas,

I'm sorry that you're still having problems.  Here's some specific questions that might help us figure this out.  Let's make it our goal to get 10.04 installed and running with the intel driver without boot parameters (and without a secondary monitor) first, and we'll worry about the wireless card later.

In the following questions, when I refer to booting with kernel parameters, I mean that you're not permanently changing the grub menu item, but you're manually editing the kernel parameters each time you boot.

1.  Are you installing from the 10.04 live CD?  I installed from a bootable 10.04 USB, but I don't think that should matter.  (If you have the time and inclination, you might want to try it).

2. You can boot the live environment (presumably a CD or USB) with the "i915.modeset=0 xforcevesa" parameters, correct?

3. Once you're in the live environment, you're able to complete the installation process, correct?

4.  When you reboot into the installed environment without adding any kernel parameters, the screen goes completely black and only a hard reboot will work, correct?

5. You can reboot into the installed environment by *just* using the "i915.modeset=0" kernel parameter correct?

6.  Your /etc/X11/xorg.conf file has a line in it that specifies it is using the vesa driver at this point, correct?  If you can get this far, post a copy of your /etc/X11/xorg.conf file so I can verify that we're on the same page.

7.  Next install the backported maverick kernel as described in the other post.  After that is finished, post the output of the command `uname -r`.

8.  Modify your /etc/X11/xorg.conf file as specified (change 'vesa' to 'intel'), post it and reboot.

Now at this point, you're saying you still get a black screen?  And if you turn it off, plug in an LCD monitor, and start it up again then both monitors are working (along with Compiz)?  And now if you unplug the external monitor the original monitor is still working?

I hope we can get it working for you!

---

### Post by acroporas on 2010-08-24
> **semmypurewal said:**
> 
1.  Are you installing from the 10.04 live CD?  I installed from a bootable 10.04 USB, but I don't think that should matter.  (If you have the time and inclination, you might want to try it).


I'm installing via the CD.

> 
2. You can boot the live environment (presumably a CD or USB) with the "i915.modeset=0 xforcevesa" parameters, correct?

Yes.  It needs both.
> 
3. Once you're in the live environment, you're able to complete the installation process, correct?


Yes, installation goes smoothly.
> 
4.  When you reboot into the installed environment without adding any kernel parameters, the screen goes completely black and only a hard reboot will work, correct?


Yes

> 
5. You can reboot into the installed environment by *just* using the "i915.modeset=0" kernel parameter correct?


yes

> 
6.  Your /etc/X11/xorg.conf file has a line in it that specifies it is using the vesa driver at this point, correct?  If you can get this far, post a copy of your /etc/X11/xorg.conf file so I can verify that we're on the same page.


Yes, it is vesa

```

Will add code later

```

> 
7.  Next install the backported maverick kernel as described in the other post.  After that is finished, post the output of the command `uname -r`.

8.  Modify your /etc/X11/xorg.conf file as specified (change 'vesa' to 'intel'), post it and reboot.

Right now I'm working on getting the computer back to a workable state.  I probably won't get around to trying this again until tomorrow.
> 
Now at this point, you're saying you still get a black screen?  And if you turn it off, plug in an LCD monitor, and start it up again then both monitors are working (along with Compiz)?  And now if you unplug the external monitor the original monitor is still working?


Ok, computer is off.  No external monitor plugged in.  Boot the computer, screen goes black.

Then I attach an external monitor, the instant I plug the external monitor in, the built-in display comes to life.  Compiz automatically enabled and functioning.  At this point but I can unplug the external monitor and the built-in display continues to function.  

Some other notes.

 - Closing the lid causes crash that requires hard reboot.
 - I was able to get both the external monitor and the built-in display to work simultaneously, but it is not instantaneous.  I had to go to display properties and click detect displays before the second display would come to life.
 - Booting with the external display attached...Only the external display worked until I opened the display properties and clicked detect displays.

---

### Post by semmypurewal on 2010-08-26
acroporas:

Have you had any luck?  It occurred to me that you might want to try automatically reconfiguring X11.  It sounds like everything is working, but for some reason your display is not configured correctly.

Note that these instructions will not work if X is running, so start by booting into recovery mode for your kernel (from the grub menu).  When you get to a root prompt try this:

```

X -configure

```

This should create a new xorg.conf file based on your current video card.  If you're in recovery mode, it should be located at /root/xorg.conf.new

Take a look at it and make sure it's using the intel driver.

You'll need to manually copy it over your old configuration.  Try this:

```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BACKUP
cp /root/xorg.conf.new /etc/X11/xorg.conf

```

The first line backs up your old xorg.conf file.  The second line copies the new xorg.conf file to your old one.

Now when you reboot, it should load the new xorg.conf file which should include your default display.

Let me know if this works for you, and I'll update my instructions in the other thread.

---

### Post by klsitton on 2010-09-13
> **acroporas said:**
> I think that it is VERY unlikely that an NVIDIA driver would work well on an Intel graphics card??  Additionally, external monitor plugged into the VGA port has the same black screen problem...
Whatever.  Mine works.  Sorry I couldn't help you...

---

### Post by waabox on 2011-04-05
I install the beta 11 and the graphics works fine.
Also, I have another problem related with the wireless card.
I made a fix,
[http://ubuntuforums.org/showthread.php?t=1722448](http://ubuntuforums.org/showthread.php?t=1722448)

if you have any question, shoot it

---

