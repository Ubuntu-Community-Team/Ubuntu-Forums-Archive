---
title: "UNABLE TO MOUNT DEVICES after &quot;Safely remove&quot;"
date: 2010-02-18
forum: Desktop Environments
---

### Post by manolomanolo on 2010-02-18
Hi to all.

As the title says, I have found almost no way to mount devices after "safely remove".
I am do able to mount back those devices (a micro SD card and a USB SATA hard drive) in case of unmounting them with "Umount" or "Eject" buttons in Nautilus. In those cases the devices are mounted, for example, just with unplugging and plugging them back.

Actually, in case of the USB SATA hard drive, I am able to mount it after "safely remove" just in case of running "sudo mount -a" from terminal. It does not work with the "micro SD" card. The "solution" in this case is restarting Ubuntu!!!

Any suggestion, please?
Thanks.

---

### Post by mcduck on 2010-02-18
Thats' how it's *supposed to* work.

If you wish to just unmount the drive, then use "unmount". The "Safely Remove"-option not only unmounts the drive but also cuts power from it, so you can't remount it again ubless you disconnect the drive and plug it back again.

Or do you actually mean that if you use the "Safely Remove"-option you can't get the drive to work again even after you have disconnected the drive and plugged it back again?

---

### Post by manolomanolo on 2010-02-18
mcduck, thanks very much for your interest in my question.

Unfortunately, as I said, it doesn't work with "my micro SD" card: unplugging and plugging back does not mount it.
As I said, the "solution" in this case is **RESTARTING the system!** :-(

---

### Post by Julita on 2010-02-18
The best way to mount anything is via the terminal. First, you have to see how the system recognizes your SD card. It should be /dev/sdbX (X - number of your SD Card as it is seen by your system) In order to mount the SD disk properly and to see errors, if there are any, type
```
sudo mount /dev/sdbX /media/your_directory
``` See the outcome of the command

If you want to create directory specifically for your card, type in terminal
```
sudo mkdir /media/sd
```
Presumably, the system would recognize your SD card as /dev/sdb1 (if you don't have any USB plugged in)

---

### Post by manolomanolo on 2010-02-18
I am looking for a "use friendly" solution.

I am not going to tell the daughter of a friend of mine (10 years old!) to mount and unmount devices using the terminal!
I'd rather consider it as a bug instead of tell the children to make that kind of tests...

Thanks for your time. Hope you can suggest "user friendly" solutions rather than nerds workarounds :p

---

### Post by mcduck on 2010-02-18
> **manolomanolo said:**
> I am looking for a "use friendly" solution.

I am not going to tell the daughter of a friend of mine (10 years old!) to mount and unmount devices using the terminal!
I'd rather consider it as a bug instead of tell the children to make that kind of tests...

Thanks for your time. Hope you can suggest "user friendly" solutions rather than nerds workarounds :p

You should probably try that "nerd workaround" for now, because it will actually give you usefull stuff like error messages etc. that would help to solve your problem.

It's hard to find out what's causing your problem without any real information about what's going on the system. In that kind of situations doing things from a terminal is pretty much always the best way to find out what's the underlying problem.

(I'm not suggesting that you should tell your friend's daughter to do that, or even that you should do it youself every time you need to mount a drive, but that you should do it once, to get more information about the situation).

Anyway, a simpler way to get usefull info about your problem would be this:

Open a terminal, and run "tail -f /var/log/syslog". Then plug in your memory card, wait until it's mounted, then use the "safely remove"-option, unplug the drive and plug it back again. After that attach the output from the terminal here.

edit: What kind of reader are you using for your SD card? Because I don't even have any option for "Safely Remove" for SD cards, only "Unmount".

---

### Post by efflandt on 2010-02-18
It is not clear what type of connection you have that you are trying to "Safely Remove".  If you have a built-in multi-memory reader, connected internally by USB, you should NOT "Safely Remove" it in Windows or Linux, because that makes the USB reader totally inactive (and/or powers it down).

If you Safely Remove any sort of external USB memory or reader, simply unplugging it from USB and plugging it back in should work (always works for me for USB memory sticks, card readers, or external hard drives).  But Unmount (umount) should be sufficient, because that makes sure that the drive or memory is sync'd (any writes are completed).

---

