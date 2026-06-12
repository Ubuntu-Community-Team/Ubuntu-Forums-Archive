---
title: "[SOLVED] Palm M515 not syncing in Gutsy Ubuntu"
date: 2007-10-27
forum: Desktop Environments
---

### Post by jarnomn on 2007-10-27
I didn't find any Gutsy (7.10) related threads on Palm sync problem so I created a new one. 

I have a problem in Syncing Palm M515 with Ubuntu 7.10.

When I press Sync button I can see USB events in dmesg:

[ 2073.703036] usb 2-2: new full speed USB device using uhci_hcd and address 4
[ 2073.876074] usb 2-2: configuration #1 chosen from 1 choice

But nothing happens after that. I don't see any events in gpilot daemon log and device will not start sync operation.

When I sync my Garmin IQue everything works fine. 
So gpilot itself is running just fine, but for some reason it will not talk to my M515.

I have the device type set to "USB:", if I change that to /dev/TTYUSB0 the gpilot daemon pops up a dialog in sync that says that I don't have Visor USB serial module installed and I should be "USB:" device. So gpilot is getting the USB events.

I did not find Visor module with apt-cache search, so I assume that Visor USB serial is no longer supported.

Any ideas how to solve the problem?

---

### Post by jarnomn on 2007-10-27
I managed to solve the problem myself :)

The issue was that the Palm M515 belongs to my wife and I had created her account with "adduser" instead of Ubuntu GUI tool. And of course I had tried M515 sync only with her account.

And it seems that gpilot is dependent on some privileges that are given by default by Ubuntu "User Settings" tool.

So if anyone else encounters similar problem, make sure that user has all the default rights needed for gpilot to work.

---

