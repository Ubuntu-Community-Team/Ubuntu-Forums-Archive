---
title: "Feisty Randomly Freezing - debug log information. Bluetooth device?"
date: 2007-10-08
forum: Desktop Environments
---

### Post by beechmore on 2007-10-08
Hello,

My Ubuntu Feisty keeps freezing. I've updated the bios on my motherboard (K8S-MX) to the latest version and I've also re-installed Ubuntu about 10 times.

I checked the system logs today and spotted the following debug line which seems to occur at the same time as the freeze:

<debug info>^I[1191841028.866860] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth').

As far as I know I don't have any bluetooth devices although I do have a bluetooth socket on my mobo.  Could this be the cause or could it be something totally different? Any help or advice would be much appreciated.

Thankyou

beechmore

---

### Post by mkoyle on 2007-10-10
If it is attempting to start bluetooth, blacklisting the bluetooth module might fix it... I don't really know.  

Anyway, to disable the bluetooth kernel module (and possibly prevent hal from polling for a bluetooth device) try the following in a terminal: 

 ```
gksudo gedit /etc/modprobe.d/my_blacklist
```

Then put this in the new file:

```
blacklist bluetooth
```

and then reboot.

If that fixes it, great; if not... with any luck gutsy's release in a week or so will do it... you could try installing gutsy now.  Of course, someone smarter than myself might have some other ideas, too.

Anyway, to undo that (if it didn't work) delete the file we just created by running

```
sudo rm /etc/modprobe.d/my_blacklist
```

--Matthew

---

### Post by mkoyle on 2007-10-10
If it doesn't work, you might just want to give the gutsy beta a try... [http://cdimage.ubuntu.com/releases/gutsy/tribe-5/](http://cdimage.ubuntu.com/releases/gutsy/tribe-5/)

Only DVD's now... it is a bit of a big download.  I recommend the DownThemAll firefox extension to make sure you can suspend/restart that download if you try to download it directly.  [https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

..............And may the force be with you.

--Matthew

---

### Post by soxs on 2007-10-11
[http://ubuntuforums.org/showthread.php?t=412125](http://ubuntuforums.org/showthread.php?t=412125)
this thread maybe realted to your problem.. I aswell get messages about wlan, which my PC does not have.

---

### Post by beechmore on 2007-10-12
Thanks for the information. I think I'll give Gutsy a try when it's released. According to the pre-release notes it has much better problem identification and reporting tools which should help me find out what's causing the freeze ups.

By the way, I tried different APIC NOAPIC etc parameters in the grub boot up file and this has helped a lot - Ubuntu only freezes occasionally now instead of every 20 minutes or so. Not an ideal solution though.

Thanks again.

Beechmore

---

### Post by Low Life Rising on 2007-10-12
Hi,

Just want to say that I am experiencing the same thing with the same message in the debug log. However I don't have it happening every 20 minutes - some days it doesn't happen at all even. The irriting thing is, I never even use the bluetooth thing :mad:

Thanks for the blacklist advice, hoping it works...

---

### Post by beechmore on 2007-10-24
Hello,

I tried everything without success - loaded ubuntu gutsy, flashed the bios, added a new board battery, messed around with acpi settings. removed the graphics card and used the on-board graphics chip and I even tried a different hard drive. In the end, I swapped the ASUS K8S - MX motherboard for an MSI KSMM3 board and the problem has gone and the system seems very stable.

I don't think the ASUS board was incompatible with anything, I just think it was simply malfunctioning.

If anyone else is having a similar problem, one possible clue to it being the motherboard is that it seemed that the computer had  to be warmed up before it became reasonably stable. When switching on for the first time each day, I had to reboot five or six times before ubuntu loaded successfully but once I got to this stage, the computer was reasonably stable.

Thanks for the input everyone.

beechmore

---

### Post by mkoyle on 2007-10-27
Thanks for the update; glad you are able to work again.  Hardware failures can be annoying.

--Matthew

---

