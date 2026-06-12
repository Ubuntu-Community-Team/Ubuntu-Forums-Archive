---
title: "DWL-122 wireless usb and NDISWRAPPER"
date: 2006-03-13
forum: Desktop Environments
---

### Post by dustynus on 2006-03-13
I have a DWL-122 wireless usb adapter.
I have ndiswrapper installed correctly.
When I do:

@basement: ~/Desktop: sudo ndiswrapper -i netprism.inf
Installing netprism
@basement: ~/Desktop: ndiswrapper -l
Installed ndis drivers:
netprism        invalid driver!
@basement: ~/Desktop: 

Why does it say "invalid driver!", what does this mean, I downloaded the "netprism.inf" file from: [ftp://ftp.dlink.com/Wireless/dwl122/Driver](ftp://ftp.dlink.com/Wireless/dwl122/Driver)

??

---

### Post by htinn on 2006-03-13
I assume you mean this type of thing:

[http://ubuntuforums.org/showthread.php?t=106846](http://ubuntuforums.org/showthread.php?t=106846)

I wouldn't mess with ndiswrapper. I use the serialmonkey driver myself (latest CVS version) and it worked fine for both Ad-Hoc and Managed modes. You will need to have "linux-headers-2.x.xx-xx" and "gcc" installed so you can compile it.

---

