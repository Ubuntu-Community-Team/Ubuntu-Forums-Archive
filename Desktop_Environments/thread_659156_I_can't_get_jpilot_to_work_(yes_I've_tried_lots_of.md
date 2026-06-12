---
title: "I can't get jpilot to work (yes I've tried lots of the posts)"
date: 2008-01-05
forum: Desktop Environments
---

### Post by beachedwhale on 2008-01-05
I have Ubuntu 7.10.  And, a Palm Tungsten E (actually I also have a later model Palm with bluetooth, but I won't even attempt that!) that I want to sync with USB.

I've done this and many variants of it:

[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

This page isn't very clear.  It says vague things like "For Ubuntu 5.10...", then I sit here and wonder "Do they really mean exactly that version, or do they mean every version after that too?  Maybe its out of date and they really mean all later versions too, I dunno."  Despite the vagueness, I've tried a bunch of variants.

And I've installed jpilot (of course).  Should I be using gnome-pilot instead? I'm not sure how the products differ.

Nothing will sync, ever.  Not if initiated from jpilot, or from the Palm device.  There's never anything at /dev/pilot so I don't know what that's supposed to be all about.  I've rebooted a few times.  I've done that sudo modprobe visor thing.  Nothing seems to produce results any different than if I had done absolutely nothing at all other than connect the device and try to sync.

jpilot's sync button always gives me this error:

****************************************
 Syncing on device /dev/pilot
 Press the HotSync button now
****************************************
pi_bind error: /dev/pilot Too many levels of symbolic links
Check your serial port and settings
Exiting with status SYNC_ERROR_BIND
Finished

The error is instantaneous so I have no actual time to press the HotSync button.

If I press hotsync, it says the connection could not be established.

OK, I give up... How do I get this to work?

---

### Post by beachedwhale on 2008-01-05
The dmesg command outputs this when I press HotSync:

[ 1661.824597] usb 1-1: new full speed USB device using uhci_hcd and address 9
[ 1661.992374] usb 1-1: configuration #1 chosen from 1 choice
[ 1661.997268] visor 1-1:1.0: Handspring Visor / Palm OS converter detected
[ 1661.997609] usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
[ 1661.997801] usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB1


So, "something" is going on.  What's this trying to tell me?  The jpilot sync button still just gives that error.

---

### Post by beachedwhale on 2008-01-05
Ack!  It figures I only start making progress on my own after I post.  I tried putting "usb:" in the port field of jpilot, and then the install user menu item and sync button does something (and requires I press the HotSync button on the device).  Odd, I tried usb: earlier but it didn't work.  I'm not sure why its doing better now.

---

### Post by Steve1961 on 2008-01-05
I can't help with j-pilot I'm afraid as I've never managed to get it to work.  However, I've found that gnome-pilot with evolution works seamlessly (OK, very occasional lock-ups but nothing that restarting gnome-pilot hasn't fixed) in Gutsy with my Palm TX.  I just added the gpilot applet to my Gnome panel and followed the instructions.

---

### Post by beachedwhale on 2008-01-05
Perhaps a dumb question, but how do I get KeyRing plugin to work?  I installed jpilot-plugins and now jpilot has a KeyRing section.

So.... how do I get some kind of KeyRing app onto the device so it has something to sync with?  I couldn't find anything on jpilot.org or [http://gnukeyring.sourceforge.net](http://gnukeyring.sourceforge.net) so I'm not sure how they're expecting anyone to figure this out.

---

### Post by beachedwhale on 2008-01-05
I'm right... its dumb... I needed to do a separate download of KeyRing from source forge, then install that using JPilot.  (I'm used to Turbo Passwords that works on Windows and is a single install.)

---

### Post by pavpan on 2008-01-05
I'm glad you found out how to make jPilot work. Note that gnome-pilot works perfectly with the Tungsten E (I have that model) and syncs to evolution and all. So you may want to try that and see if you like that program better.

---

### Post by beachedwhale on 2008-01-05
Do you know if gnome-pilot has a password keeper program available that'll sync between Ubuntu and Palm OS?

---

### Post by axel112 on 2008-02-01
> **pavpan said:**
> I'm glad you found out how to make jPilot work. Note that gnome-pilot works perfectly with the Tungsten E (I have that model) and syncs to evolution and all. So you may want to try that and see if you like that program better.

How have you configured gnome-pilot? I am having problems with my tungsten.

---

### Post by geomantic8 on 2008-02-03
Same troubles here: can't sync my Palm Tungsten E with either jpilot or gnome-pilot. 

I get this error: 
pi_bind error: /dev/ttyUSB1 No such file or directory
Check your serial port and settings

Is it the security on the Tungsten E device? Or is due to priveleges on /dev/tty* ?

Thanks,
-g8

---

### Post by geomantic8 on 2008-02-06
Well, progress on getting it to sync with gnome-pilot using the how-to posted above. But I really don't use Evolution, so it's not much of a consolation, since what I *really* want is jpilot as a backup to my contacts, memos, calendar.

---

### Post by axel112 on 2008-02-21
Have you tried /dev/ttyUSB0 instead of USB1?

---

