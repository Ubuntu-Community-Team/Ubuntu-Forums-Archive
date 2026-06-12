---
title: "Problems Booting from Live CD (Black Screen with Blinking Cursor)"
date: 2012-07-29
forum: Desktop Environments
---

### Post by horizons187 on 2012-07-29
The title pretty much says what's happening. I've installed Linux multiple times on multiple machines but this new desktop I bought refused to boot from wubi. I then decided that I would do a full install as I really wanted a seperate partition anyway and afterwards I got the same issue as I had with wubi on the live cd. 

It will show the purple screen with the ram = human logo but afterwards goes to a black screen with a blinking _ cursor. It does not respond to keyboard presses.

I am on a Gateway DX4860

NVIDIA GeForce GTX 550ti

Intel r core tm i3-2120 quad core 3.30 Ghz

8 GB of RAM

Windows 7

If you need any additional information I would be happy to give it.

---

### Post by TheFu on 2012-07-29
I couldn't find any solutions based on that specific Gateway model. Thanks for providing it - extremely helpful.
At this point, there isn't enough information to help, so we need to gather more.

During the boot sequence, start hitting the ESC key over and over until the splash screen disappears.  Look for errors at the different stages and write them down.  Perhaps then you will be able to see the specific error(s) on the screen and will be able to find solutions?

If grub isn't starting, perhaps a disk partition or controller incompatibility issue?  I'd attempt using the liveCD off a USB flash drive instead to get passed the HDD recognition issue to gather more information about the hardware that Linux actually sees using **lshw**.

Does 10.04 work on this hardware?  Have you tried any other Linux distros like Debian, Puppy or DSL? Did they work?

---

### Post by horizons187 on 2012-07-29
I haven't tried previous versions or other distros.

I have however tried booting from a usb I do seem to get further when I do so but it freezes up somewhere around the hard drive detection on usb.

Is there anything specific I should be looking for when I get "behind" the splash screen?

*EDIT* I don't actually get to GRUB from USB either was my point. I think it might be an issue with the HDD?

*EDIT* Tried a fedora USB couldn't get it to recognize my video card and I have no VGA cable for my onboard.

*UPDATE* Created a new ubuntu USB with a freshly downloaded ISO. I can get it to a the GNU screen that lets me check disk for errors, try ubuntu without installing, and install ubuntu. After I press any option I get a black screen but I don't lose video signal.

---

