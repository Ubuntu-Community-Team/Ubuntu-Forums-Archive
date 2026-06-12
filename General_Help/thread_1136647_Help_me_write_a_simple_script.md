---
title: "Help me write a simple script?"
date: 2009-04-25
forum: General Help
---

### Post by jolindbe on 2009-04-25
Hi!

I am quite new to Ubuntu, and I have realised that I need a really simple script to remove one annoyance: I have a docking station with an external screen, so when the computer is in this docking station, it should have a different screen resolution. Using the Nvidia program, I have managed to set up two different resolution modes, and I have made two small scripts that I can run to change the resoltion. The script that needs to be run is "xrandr -s 0" for the docked setting, and "xrandr -s 1" for the undocked setting.

Now, I want this to be automated, so that a script can detect whether the computer is docked or not, and run the appropriate command line at startup. One possible way to do this detection would be to check if my external HDD, connected to the docking station, is detected. Thus, in short, I need a program that does the following:

if external HDD detected
    xrandr -s 0
else
    xrandr -s 1
end if

How do I write this script (especially the first line...)?

Thanks for any help!

---

### Post by StOoZ on 2009-04-25
how do you connect to the docking station? is it via a proprietary  connector? usb?

---

### Post by jolindbe on 2009-04-25
> **StOoZ said:**
> how do you connect to the docking station? is it via a proprietary  connector? usb?

It is a Dell docking station, I put the computer onto a device that looks like this: [http://www.laptopbatteries.co.nz/images/categories/Dell-dockingstation.jpg]("http://http://www.laptopbatteries.co.nz/images/categories/Dell-dockingstation.jpg")

Edit: And the external HDD is connected to this docking station by USB, and is always automatically detected by Ubuntu, an icon is put on the desktop. Is it possible to run a command and ask if this special USB unit is connected? Could I perhaps put a file with a strange name on the drive, and if it can find this file, it knows it is in docked mode? Or is there a more simple way?

---

### Post by jolindbe on 2009-04-26
I managed on my own. Here's the script if anyone's interested.

```
#!/bin/bash
lsusb -d 046d:c501;
if [ $? == 1 ]; then
	xrandr -s 1
else
	xrandr -s 0
fi
```

where 046d:c501 is the ID of my USB device.

---

