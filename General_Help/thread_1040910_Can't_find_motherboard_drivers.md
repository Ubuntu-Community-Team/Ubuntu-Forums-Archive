---
title: "Can't find motherboard drivers"
date: 2009-01-16
forum: General Help
---

### Post by Tribulation on 2009-01-16
I've recently built a new computer and installed Ubuntu on it. Ubuntu found the video card drivers easily, but I don't think it did the same with my motherboard. My audio is really quite, and I've been looking for motherboard drivers to see if they'd help. I'm having a hell of a time finding them though. Could anyone point me to a site where I can download drivers for a Gigabyte GA-EP43-DS3L?

---

### Post by Zack McCool on 2009-01-16
There aren't "motherboard drivers" to download.

It sounds like your audio drivers are already installed.  A symptom of the wrong driver would be no sound, and likely an error message.  You are getting sound, but at a lower than expected volume.

This is likely a settings issue.  Open the volume control, go to Edit|Preferences, and make sure that everything you might need has a check box.  Of particular importance will be Master and PCM.  Also, if there are individual speaker controls (front, rear, center, etc...) you might want to select these as well.

When you accept those settings, the volume control will have expanded quite a bit.  Now, make sure that PCM and Master are up high, or max.  Make sure that at least one of the individual speaker controls is at max, and the others are mixed to get you proper audio distribution.  

If everything is good, you should have decent volume now...

---

### Post by Tribulation on 2009-01-16
Thanks. I feel like a moron (PCM wasn't high enough, and neither was another one of the speaker options) but thanks. One other question. You said there are no motherboard drivers to download... why do you say this?

---

### Post by Zack McCool on 2009-01-16
Because there are none.  Linux isn't Windows.  Things are done differently.  In Linux, hardware support is mostly built into the kernel (well, using modules that get loaded when needed).  

There is no such thing as a "Motherboard" driver, even in Windows.  A motherboard is a collection of other devices.  You have a bus, an IO controller, a disk controller, a video card, an audio card, and so on.  They just happen to all be on the same board.  What linux does is include all of these drivers as kernel modules.  

Now, if you happen to come across a state of the art motherboard that has, perhaps, a new bus controller that doesn't have a kernel module in the current version, you may need to download the source for one and compile it into your kernel (if it is available), or wait for a new kernel release to support your new hardware.

This is fairly uncommon for anything except for video, wi-fi and things like webcams.  Occasionally, you'll also run into a new sound card that doesn't work, either.  Since manufacturers rarely support linux directly, you are usually forced to wait until the kernel includes support for that device...

---

### Post by Zack McCool on 2009-01-16
Oh, and as for the PCM setting, don't sweat it.  Certainly not even approaching the level of moron there.  PCM is a bad label for what should be the "Master" volume...   It confuses people all the time...   ;)

---

### Post by jocko on 2009-01-16
> **Tribulation said:**
> You said there are no motherboard drivers to download... why do you say this?

All drivers that are needed for the motherboard are already part of the linux kernel, with a few exceptions for very new hardware that haven't got any driver yet or some pieces of hardware for which there are no open source drivers.
You would notice if a driver was missing, as this would mean some of your hardware would not work at all.

---

### Post by Tribulation on 2009-01-16
Thanks for clearing that up for me.

---

### Post by Zack McCool on 2009-01-16
Any time...

---

