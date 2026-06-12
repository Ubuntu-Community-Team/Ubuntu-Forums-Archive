---
title: "Ubuntu not powering USB Hard Drive down"
date: 2009-03-29
forum: General Help
---

### Post by fugitive.rmx on 2009-03-29
Hi,

I recently installed Ubuntu 8.10 and while I was extremely impressed with what I saw as a first time user, there's an issue that I have searched long and hard to try and resolve, but cannot find the answer.

I have an external 1TB USB hard drive (WD elements) and whenever I would use Windows XP to 'safely remove hardware' it would power down the HD so it was shut down & all the lights would turn off, then I could turn it off at the powerpoint.

I can't find out how to do this in ubuntu!  At first I thought unmounting the drive would work - but it doesn't power it down, it just removes it from the desktop...

Can someone please tell me how to power it down from ubuntu so I can shut it down without having to turn it off at the powerpoint while it's still powered up?

Thanking you in advance!

---

### Post by Ericyzfr1 on 2009-03-29
It works on mine, I have 2 partitions on it and as soon as the second one is unmounted, it shuts-off.

---

### Post by Sidewinder1 on 2009-03-29
Once it's unmounted it's OK to manually power it down. I have a 1TB WD drive and every once in a while I forget to unmount before I log off and shut my machine down. Then I say aw $h1t and turn it off manually with no problems.
HTH
Side

---

### Post by fugitive.rmx on 2009-03-29
> **Sidewinder1 said:**
> Once it's unmounted it's OK to manually power it down. I have a 1TB WD drive and every once in a while I forget to unmount before I log off and shut my machine down. Then I say aw $h1t and turn it off manually with no problems.
HTH
Side

Hmmm, I really would prefer for it to be powered down, to me manually powering it down is like turning the computer off at the powerpoint before shutting it down from the O.S...and if it can be done in windows, why can't ubuntu do it?  There must be a way...

---

### Post by fugitive.rmx on 2009-03-29
bump

---

### Post by DigitalNoise on 2009-03-29
> **fugitive.rmx said:**
> Hmmm, I really would prefer for it to be powered down, to me manually powering it down is like turning the computer off at the powerpoint before shutting it down from the O.S...and if it can be done in windows, why can't ubuntu do it?  There must be a way...
I'm sure there's a way to do this, but once the drive is unmounted, the heads are parked (see WD's documentation if you don't believe me) - and it's safe to power down from the button on the front.

Window's command to safely remove hardware is very much akin to unmounting the drive - it tells the drive to park the heads and powerdown.  The reason it doesn't do this by default in Linux is because the unmount command (which is what gets issued when you unmount the drive) just unmounts and parks - no power commands are issued.

---

### Post by fugitive.rmx on 2009-03-30
> **DigitalNoise said:**
> I'm sure there's a way to do this, but once the drive is unmounted, the heads are parked (see WD's documentation if you don't believe me) - and it's safe to power down from the button on the front.

Window's command to safely remove hardware is very much akin to unmounting the drive - it tells the drive to park the heads and powerdown.  The reason it doesn't do this by default in Linux is because the unmount command (which is what gets issued when you unmount the drive) just unmounts and parks - no power commands are issued.

So is there a command in Ubuntu that I can give that will do the powerdown?  Or perhaps some kind of applet that powers it down?  I'm sure I'd be able to do it with ubuntu somehow, just for my peace of mind...

---

### Post by DigitalNoise on 2009-03-30
> **fugitive.rmx said:**
> So is there a command in Ubuntu that I can give that will do the powerdown?  Or perhaps some kind of applet that powers it down?  I'm sure I'd be able to do it with ubuntu somehow, just for my peace of mind...
Not that I'm aware of, you may have to look beyond Ubuntu.

There's a whole world of Linux out there and tons of apps.

---

### Post by fugitive.rmx on 2009-03-30
> **DigitalNoise said:**
> Not that I'm aware of, you may have to look beyond Ubuntu.

There's a whole world of Linux out there and tons of apps.

Ok, it would have been awesome if ubuntu did it...I guess I'll do as you say and look elsewhere for it.  I'm new to Linux, so anything that works in Linux should work in ubuntu?  It's all interchangeable?

---

### Post by afzalnaj on 2009-06-01
if u have found the solution, please tell me

otherwise here's a bash script

> #!/bin/bash

if [ -z $1 ]; then
    echo 'device not specified'
    exit 1
fi

DEVICE=$(udevadm info --query=path --name=$1 --attribute-walk | grep 'USB Mass Storage Interface' -B50 | grep 'looking at parent device' | tail -n 1 | cut -d"'" -f2)

if [ -z $DEVICE ]; then
    DEVICE=$(udevadm info --query=path --name=$1 --attribute-walk | grep 'USB Mass Storage Interface' -B50 | grep 'looking at parent device' | tail -n 1 | cut -d"'" -f2)
    if [ -z $DEVICE ]; then
        echo 'not an USB mass storage device'
        exit 1
    fi
fi

echo 'suspend' > /sys/$DEVICE/power/level

its supposed to suspend the usb device

taken from here:
[http://www.linuxquestions.org/questions/linux-hardware-18/usb-pen-drive-flash-drive-unmounted-but-the-power-is-there-503208/](http://www.linuxquestions.org/questions/linux-hardware-18/usb-pen-drive-flash-drive-unmounted-but-the-power-is-there-503208/)

ok this wont work, i assume the path for the device is different than that which is searched for, any experienced user plz put some light on this (i dont even have a power/level file for my mass storage device)

thanks

---

