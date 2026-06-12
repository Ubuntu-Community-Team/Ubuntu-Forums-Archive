---
title: "Softmodem :("
date: 2006-05-21
forum: Desktop Environments
---

### Post by vidak on 2006-05-21
I have an Acer 1641LMi laptop with a built-in (softmodem). 
I read on linmodems.org, that it should work with the last kernel, but I couldn't manage to make it work.
Has anyone a working softmodem under linux? Is it possible to use this type of modem with linux? (it's an Intel High Definition Audio (HDA) sound card&modem).
When at home, I got no broad-band net, just a phone cable - I am writing this message using Window$... Please, help!!!

---

### Post by Matchless on 2006-05-21
Hi,
      If you go to the Official Wiki and search for dialupmodemhowto you will find some good instructions on installing the driver for Intel modems. I have an Intel536EP running and it seems as if the Intel537EP also works. You can also try scanmodem to recognise the model of your modem. I have identified mine by reading the modem chip number, but you may have trouble doing that. The other suggestion is to get it running in windows and do a modem diagnostic on it and it may spit out the model. I have also in the past opened the windows modem driver file and found the number in the heading.
Hope this helps you.

---

### Post by vidak on 2006-05-22
Well, a lame question... I have managed to install slmodem modules, and slmodem daemon. When the daemon is running and I have made a symlink from the corresponding device (/dev/ttySL64) kppp and wvdialconf recognised the modem. However I have to run slmodemd manually specifying /dev/ttyS0 as device, as neither /dev/slamr0 nor /dev/ttySL0 (which the daemon would search for) exists.
I have no phone line this time, just LAN, so I cannot test the device... :(
What do you think, should this configuration work, or I am fooling myself, and the daemon wants to use an existing device, which is not a modem?

---

### Post by Matchless on 2006-06-17
Hi,
   I am not familiar with the HDA (High Definition Audio ) Conexant modem, but the wiki dialupmodemhowto states that these drivers may not be needed and you can only download and install sl-modem-daemon from the repositories, this is the smartlink one. See under Modems supported by Also drivers. Otherwise Linuxant sells an HSF driver with HDA support, but the 14400 speed one is free.
You can also have a look at this thread [http://www.ubuntuforums.org/showthread.php?t=160831](http://www.ubuntuforums.org/showthread.php?t=160831).

---

