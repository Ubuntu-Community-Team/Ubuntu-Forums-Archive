---
title: "Unmounting USB HDD"
date: 2006-06-07
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-06-07
I use my [Cowon iAudio x5]("http://www.goaudio.co.uk/cowon-iaudio-x5-20gb-description.html") as a USB hard drive frequently - I just plug it in via usb and it automagically gets mounted in gnome.

When I have finished using it I click "eject" to unmount it - and as far as I can tell everything works just fine.  However - there is one small glitch.  When I unmount in windows the screen (on the X5) stops showing "connected" and shows "it is now safe to disconnect".  In Ubuntu it doesn't do this - it continues to say connected.  Now I am curious as to whether this means that it is not unmounted properly, or whether windows just sends a different signal to ubuntu when unmounting, which the player cannot interpret.

---

### Post by J77 on 2006-06-07
On the command line:

**sudo umount /media/usbdisk**

(The last bit's your mount point, it'll be something like /media/??? - you can check this in your gnome file manager or in /etc/fstab.)

---

### Post by Lunar_Lamp on 2006-06-07
Hehe, I have no idea why i didn't think to try that.
Yes - the same result occurs.  So, the device is being unmounted correctly via "eject", but is just not showing up as "safely disconnect" - which is no real hardship I guess.

---

### Post by wilberfan on 2007-01-10
I just noticed this with my new iAudio X5L.   The device says "connected" whether I right-click on the icon, or whether I use the umount command...   

Nice to know there's no harm being done.  (?!)

---

### Post by sha_man on 2007-01-13
i have the same issue with iAudi X5 (with rockbox though) Any solution? Because it DOES work with windows, so i think it's an ubuntu thing...

---

### Post by dcstar on 2007-01-13
> **Lunar_Lamp said:**
> Hehe, I have no idea why i didn't think to try that.
Yes - the same result occurs.  So, the device is being unmounted correctly via "eject", but is just not showing up as "safely disconnect" - which is no real hardship I guess.

If Ubuntu is still writing cached data to the USB device, you will see a box on the screen saying something like "Unmounting in process" (or something or the other), so you are warned NOT to unplug the device if Ubuntu still needs it, otherwise the system has done its job.

Maybe a "Safe to Unplug" message would be a good thing, just to provide that extra level of reassurance - find the next version Development Forum and add it to the "wishlist"!!

---

### Post by Lunar_Lamp on 2007-01-13
I think you might have mis-interpreted where the "safe to unplug" should be.  I was talking about on the actual device itself.

---

