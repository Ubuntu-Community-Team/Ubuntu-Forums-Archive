---
title: "Device descriptor read/64 error --110"
date: 2009-01-25
forum: General Help
---

### Post by merciadriluca on 2009-01-25
Hello,

When Ubuntu launches, I receive 4 times:

**usb 3-2: device descriptor read/64 error -110**
, followed by:

**usb 3-2: device not accepting address 8 error -110**

I've noticed that my computer waits 8 or 9 seconds before launching the boot sequence. I had never had this ubuntu message (about the usb 3-2).

After receiving this message, there are some other pieces of information, but I can't read them because it goes too fast. What file do I have to look in, to see the last boot log?

I've got to add that I haven't added a new device to the P.C., and I didn't modify any USB driver.

What can I do?

Thanks!

---

### Post by merciadriluca on 2009-02-08
up

---

### Post by no_angst on 2009-04-18
I'm getting the exact same thing.

merciadriluca, are you running 8.10 on a Lenovo desktop by any chance?  I'm wondering if it could be my USB multi-slot memory card reader?

I also get the messages when the system is shutting down.

---

### Post by merciadriluca on 2009-04-19
Hello. I have found the solution. In fact, it displays this message many times because Ubuntu tries to recover from the former errors about a USB peripheral. You have (unfortunately) to disconnect every USB device you have connected to your PC, and try every possibility (begin by disconnecting all the devices, then plug in one device: if it works, continue plugging the others, if it does not work, this device is not supported at all by Ubuntu).

I'm not on a LeNovo laptop.
I'm sure you are using a SanDisk multi-card reader. Here, it was this peripheral which was not working properly, and which was causing the errors!

:-) Did it work?

---

### Post by VastOne on 2009-04-27
> **merciadriluca said:**
> Hello. I have found the solution. In fact, it displays this message many times because Ubuntu tries to recover from the former errors about a USB peripheral. You have (unfortunately) to disconnect every USB device you have connected to your PC, and try every possibility (begin by disconnecting all the devices, then plug in one device: if it works, continue plugging the others, if it does not work, this device is not supported at all by Ubuntu).

I'm not on a LeNovo laptop.
I'm sure you are using a SanDisk multi-card reader. Here, it was this peripheral which was not working properly, and which was causing the errors!

:-) Did it work?

Just started getting these same errors today.  When I disconnect the Brother printer that has worked flawlessly since I installed it on a brand new Jaunty implementation, the error goes away and I get a normal boot.

Looking at this on the web, there seems to be a long history of errors like this. Can anyone shed any light on why it lingers on and on?

---

### Post by merciadriluca on 2009-04-27
I think that, as you habitually disconnect a peripheral once it seems not to work, people are not very concerned with this kind of errors. :(

---

### Post by VastOne on 2009-04-27
> **merciadriluca said:**
> I think that, as you habitually disconnect a peripheral once it seems not to work, people are not very concerned with this kind of errors. :(

I am very concerned with this error as now I can longer print. My usb devices no longer work, except for kb and mouse.

None of the solutions I have found online work and there seems to be little push to resolution as some of the bug reports are 3-4 years old. :(

---

### Post by merciadriluca on 2009-04-27
Yes, that is precisely what I wanted to say. I cannot help you much, anyway :(:(

---

### Post by VastOne on 2009-04-27
> **merciadriluca said:**
> Yes, that is precisely what I wanted to say. I cannot help you much, anyway :(:(

Appreciate the thought! Maybe some traction can be started...:P

---

### Post by dspisak on 2009-11-04
I also had the problem (out of the blue) with the repeating error messages just yesterday.  The best part is that it affected each the three versions of linux installed on my computer (9.04 x86, 9.04 x86_64, Mint 7 Gloria).  XP Pro did not show error messages but was slower to start.

Well, I first tried reloading the BIOS, no luck.  Then I noticed during the second time ubuntu was reading the USB ports during startup that the error messages started after the system tried to load the Bluetooth module.  So, I then shut down the computer, turned off the power supply and removed the Bluetooth &#8220;tooth&#8221;.  I also exchanged the USB mouse for a PS/2 mouse but I don&#8217;t think that would make much difference.  Oh yes, the printer also was unplugged previously.  On reboot 9.04 x64 came up just like old times.  First I connected the printer and turned it on.  Success!  9.04 found the printer and loaded the correct driver and configuration.  Next came the Bluetooth, installed in a different USB port.  Success again.  It links with my cell phone as before.  A couple of reboots shows that all is well.  Apparently, something causes the USB addresses and/or assignments in the bios to be messed up.  Re-assigning devices to ports appears to correct the error.  An easy fix once you know how.

---

### Post by merciadriluca on 2009-11-05
> **dspisak said:**
> I also had the problem (out of the blue) with the repeating error messages just yesterday.  The best part is that it affected each the three versions of linux installed on my computer (9.04 x86, 9.04 x86_64, Mint 7 Gloria).  XP Pro did not show error messages but was slower to start.

Well, I first tried reloading the BIOS, no luck.  Then I noticed during the second time ubuntu was reading the USB ports during startup that the error messages started after the system tried to load the Bluetooth module.  So, I then shut down the computer, turned off the power supply and removed the Bluetooth “tooth”.  I also exchanged the USB mouse for a PS/2 mouse but I don’t think that would make much difference.  Oh yes, the printer also was unplugged previously.  On reboot 9.04 x64 came up just like old times.  First I connected the printer and turned it on.  Success!  9.04 found the printer and loaded the correct driver and configuration.  Next came the Bluetooth, installed in a different USB port.  Success again.  It links with my cell phone as before.  A couple of reboots shows that all is well.  Apparently, something causes the USB addresses and/or assignments in the bios to be messed up.  Re-assigning devices to ports appears to correct the error.  An easy fix once you know how.
Did you finally re-plug all your previously-plugged devices?

It is also often caused by a device which is not supported by the kernel, just like my multi card-reader.

---

### Post by dspisak on 2009-11-05
> **merciadriluca said:**
> Did you finally re-plug all your previously-plugged devices?

It is also often caused by a device which is not supported by the kernel, just like my multi card-reader.

I did not unplug the keyboard or the multi-card reader.  The printer was unplugged earlier due to another problem.  I did consider that the card reader, Sony internal, but when the error messages started after the system's attempt to load the bluetooth module, I decided to unplug the "tooth" - end of problem.  The problem did not return after I re-installed the tooth.

---

### Post by merciadriluca on 2009-11-05
Okay. It seems that teeth are badly supported under Ubuntu, and more generally, under Debian.

---

### Post by asuastrophysics on 2009-11-11
> **merciadriluca said:**
> if it does not work, this device is not supported at all by Ubuntu).

so you're saying ipods are no longer supported by ubuntu? my ipod is doing this :confused:

---

### Post by merciadriluca on 2009-11-11
> **asuastrophysics said:**
> so you're saying ipods are no longer supported by ubuntu? my ipod is doing this :confused:
Mmh I should have been less definitive, but this is clearly due to a support problem. Is it a ``real iPod'' (i.e. one coming from Apple)? When did you buy it?

---

