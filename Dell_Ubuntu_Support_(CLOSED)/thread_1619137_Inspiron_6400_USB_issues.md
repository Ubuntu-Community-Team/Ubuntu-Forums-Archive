---
title: "Inspiron 6400 USB issues"
date: 2010-11-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chee on 2010-11-11
So I setup 10.10 on my Inspiron 6400 and everything is great.  I used Ubuntu about 4 years ago,  then switched back to WinXP,  but migrated but to Ubuntu and am very gald I did.

I am only having one issue,  I have a USB mouse and USB TV tuner that work fine,  unless I unplug them.  When I plug them back in they don't seem to get any power or aren't recognized.  If I restart the computer eveything is fine again,  but I am wondering if there is anything I can do so that I don't have to restart just to get my ouse working (though the touchpad works fine still).

---

### Post by chee on 2010-11-12
No one else has had this issue?

No one has a tip to get the computer to scan for USB devices?

---

### Post by skooternb on 2010-11-12
Try lsusb in the terminal...  see if it recognizes anything.

---

### Post by chee on 2010-11-20
lsusb just hangs,   nothing comes up.

So I tried dmesg|grep usb and the last hundred or so lines are:
usb_set_interface failed

not sure what that means but I would appreciate any guidance.
Thank you.

---

### Post by chee on 2010-11-21
So if I reboot at first lsusb works fine and sees my mouse and HVR950Q fine.    

Not sure where to got next,  there must be something causing this,  but I have no clue how to figure out what.

Any help woudl be greatly appreciated.
Thank you

---

### Post by wprecht on 2010-11-22
Sounds like a conflict, but I am not sure where to begin running that down.  I assume you've done things like try the other ports since you have 4? They probably all feed the same controller.  If there is a way to bounce the USB monitor, then that would be and option. 

I don't have a Tuner,  but my m6400 has had few few problems with the various other devices I've tried.

---

### Post by chee on 2010-11-22
For the last 2 days I have had no issues,  not sure what the problem was but it isn't happening now.

---

### Post by chee on 2010-11-23
OK for some reason today I had a problem,  is there anyway for me to see what just happened?   I hadn't used the tuner card yet today,  tried TvTime,  nothing happens but I haven't been able to get that working lately anyways,  so I tried Me-TV,  can't find video,  tried Kaffeine,  same issue.  So that is when I thought that the USBs were going a little haywire again,  I tried lsusb,  it just hangs,  so I restarted my computer.  Now lsusb works fine (though my tuner is listed but not working).

So,  I realize the tuner issue is probably a different thing,  but this USB problem is getting annoying.  If anyone can point me in the right direction for troubleshooting this I would be very appreciative.

Thank you

---

### Post by chee on 2010-11-27
So I switched to 10.04 and the issue is gone.  I have no idea what the problem was but oh well I guess.

---

