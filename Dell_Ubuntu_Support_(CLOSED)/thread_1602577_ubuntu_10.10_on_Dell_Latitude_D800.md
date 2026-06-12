---
title: "?ubuntu 10.10 on Dell Latitude D800"
date: 2010-10-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rogowar on 2010-10-21
I have been unable to get either the wireless NIC (Broadcom 1120) or the video (Nvidia) working in any of the 10.10 variants (ubuntu or x... or k...).  I did see that the broadcom proprietary driver was available and installed it, but that didn't work.  

So, in a fit of pique (after doing like 5 different installs), I opted for Kubuntu 10.04, which had, if anything, more extreme video artifacts than 10.10.  Fortunately, I checked the hardware drivers available, and both the Nvidia and Broadcom drivers were available.  I was very pleased, upon restart to find everything working.

Unfortunately, I ran all the updates and was told that the Nvidia driver had no usable configuration.  When I followed the prompts to create a new configuration, the display artifacts are back.  

Any ideas how to return the the pre-update Nvidia configuration?

---

### Post by P4man on 2010-10-21
Can you give a bit more information what happens now? You boot in to a command line?

You could try moving your current xorg.conf,

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.bad
```

Note the capitalization of X in X11.

Then  let nvidia driver create one:

```
sudo nvidia-xconfig
```

then reboot or restart X:

```
sudo service gdm start
```
(or restart if it says its already running)

---

### Post by rogowar on 2010-12-13
That was actually one of the things I attempted.  When I run the restart of the xserver, I end up getting dumped to a pure command line.  Whenever I restart the machine, I'm confronted with the dialog box "Ubuntu is running in low-graphics" mode error, stating Screen(s) found, but none have usable configuration.  I can then Run Ubuntu in low-graphics for one session, Reconfigure graphics, Troubleshoot error, Exit or Restart X.  

When I review the troubleshooting, I can see from the xorg log "Failed to load NVIDIA kernal module".  Is it possible the version of NVIDIA driver is incompatible with the new kernal?  I also see in the startup log that xf86OpenConsole:VT_WAITACTIVE failed: Interrupted System Call.

---

### Post by rogowar on 2010-12-13
I had success following this workaround for the xorg.conf file:

[http://ubuntuforums.org/showpost.php?p=9955270&postcount=6](http://ubuntuforums.org/showpost.php?p=9955270&postcount=6)

---

### Post by alancain on 2011-02-15
I also have a dell latitude d800, and had horrid issues with the pointer and other display artifacts. I made one final attempt, prior to harikiri, to get the nvidia driver and the pointer problem is now resolved. My personal glee aside, do try to get the driver again; perhaps it is updated and will work for you now. My broadcom wifi is working now as well.

Good luck to you, and keep at it. The system is working flawlessly now.

Alan:p:p

---

### Post by sumps on 2011-12-04
Hi Alan, you say that you got it working but you don't say what you did  !! I guess it is too long ago now for you to remember, but this weekend I  tried to get my old D800 doing something useful again and installed  10.10 after unsuccessfully trying to install 11.04.

I got the background with the vertical lines, series of dots around the  mouse pointer, no Broadcom Wi-Fi and a mouse pointer that kept moving of  its own accord to the top right corner of the screen - only to be  temporarily brought back under control by a hard push down on the track  stick. All, it would appear from various posts I have read, classic  symptoms of trying to run Ubuntu 10.10 on a Dell D800.

The nvidia-xconfig definitely does not work on 10.10 and I could only  sort out my D800 by going back to 10.04 (which is better than nothing).  Then when I used the system>administration>hardware drivers app to  install the 3rd party Nvidia and Broadcom drivers everything worked  fine apart from the "self propelling" mouse pointer.

It seems that the older Broadcom and Nvidia (96 version) drivers  supplied with 10.04 are OK but that the newer drivers with 10.10 are not  working correctly with the Dell Latitude D800. This is a bit of a shame  and if anyone can suggest a work around it would be great. I tried the  changing "Nvidia" to "Nv" in the Xorg.conf file fix that I had read and  this worked but I then had no control over the resolution which was  stuck on low res VGA or SVGA.

I still have a mouse cursor with a mind of its own, despite using trying  an Xinput fix that is not permanent, looking to see if I could  Blacklist the module and installing and trying a few Touch Pad  applications.

So near and yet so far, I'll keep trying but if anyone has any ideas it  would be appreciated.

---

### Post by sumps on 2011-12-09
I have now cracked the problem with the wayward mouse pointer. I used the Xinput fix but put it in the Startup Application that you can find in the "Preferences Menu". Basically you create a new Startup Program and copy the following text...

xinput -set-prop "DualPoint Stick" "Device Enabled" 0

....in to the command box.

I gave my new Startup Program a name "TrackStick Disable" so that I remember what it was in the future and added a comment as a memory jogger and it works like a charm. Every time I reboot the command is run and I never get the wandering cursor ever again.

---

