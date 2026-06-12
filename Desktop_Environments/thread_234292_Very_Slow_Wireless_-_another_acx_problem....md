---
title: "Very Slow Wireless - another acx problem..."
date: 2006-08-11
forum: Desktop Environments
---

### Post by GTar on 2006-08-11
Ok, I've seen the types of problems that people have had with this chipset, especially when upgrading to 6.06. I've just managed to get my wireless card (DLink DWL-520+) working using the following method:

Added the line 'options acx firmware_ver=1.2.1.34' to the file '/etc/modprobe.d/options'and rebooted. After setting the card up using the default Ubuntu Network tool, the card appeared to work...

...EXCEPT it is preforming horribly! The speeds are never above 10kbs and it is constantly dropping or timing out. Also, when I try to shutdown the computer, I get a screen full of the following:
```

<bunch of numbers> acx: BUG: no free txdec left
```

Any ideas? What on earth does this error mean?

I know for a fact that the wireless card is working fine as I'm using it right now to post this message from XP. Any help would be appreciated.

---

### Post by Neobuntu on 2006-08-11
Until stable...

sudo apt-get install ndis-gtk

Copy the XP drivers into you home directory and into a folder with a short name like "wifi."

...Do this via non-wireless ethernet if you have to (else go to the XP driver directory in a terminal and "ndiswrapper -i WHATEVER.inf") Use "-h" for help.

Put the acx into the blacklist text file "/etc/modprobe.d/blacklist".

Note: I use "kdesu konqueror" (and set to show the / directory on start up) to quickly find and edit config files with Kate. It's pointy clickier. :)

Run the "Install Windows Drivers" and point it to your XP driver for the given (cheap arse) device. 

Put "ndiswrapper" at the top of /etc/modules to start after boot (instead of acx as it is now blacklisted from auto starting.)

Note you may/will have to do this again after an automatic kernel upgrade but the "ndis-gtk" package (That yields "Install Windows Drivers") makes it easy!

Oh and blame TI for making win-ony crap and not sharing. ALWAYS check ubuntu automatic compatibility BEFORE buying a device. But you prob know that right? (Crappy chip-sets)

Never forget tah one can spend $10 and replace the device with one that has ZERO driver setup in (K)ubuntu.

---

### Post by GTar on 2006-08-11
Ok, thanks for the suggestions. I've tried ndiswrapper before and tried again last night without any success.

I don't think the problem is so much that it wont work. Like I said, this is a reinstall. I've had the card working fine in previous versions of Ubuntu. The problem is that it's incredibly slow, and things time out constantly.

I know it's not the connection, I have another Ubuntu system on the network with the same wireless card working fine. Could anyone suggest maybe what that error message means and why on earth it's so slow?

---

