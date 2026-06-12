---
title: "Kernel ACPI bugs with dell optiplex 320"
date: 2010-12-21
forum: Desktop Environments
---

### Post by xorkid on 2010-12-21
Hi Folks!

I'm trying to get WOL (Wake On Lan -suspend and hibernate don't work either) working in Ubuntu 10.10 amd64 on the above computer for a family member but seem to not be getting anywhere! 

WOL is enabled correctly I verified that after shutting down in windows XP that the computer came on with WOL.

I have tried the following:

enable wol
```
ethtool -s eth0 wol g
```
the computer shuts-down but won't wake up by WOL packet

make sure the Ethernet (MAC0) can wake up PC
```
echo "MAC0" > /proc/acpi/wakeup
```
the computer shuts-down but won't wake up by WOL packet

kernel parameters:
```
acpi=off
```
```
apm=power_off acpi=off
```
```
acpi=nopci
```
with all of the above, the computer doesn't not power down after shut down. the power button light is still on and has to be pressed to turn it off. Here is the strange thing: WOL works after manually tuning it off! I tried inserting apm module but it is not available.

can anyone help me to get WOL working?

Thanks in advance!

---

### Post by xorkid on 2010-12-22
can anyone help or suggest where else I could get help?

---

### Post by Mr-Badger on 2011-08-02
It has been a while since this was posted, but if this helps, great :) I am using an Optiplex320 at work running Natty.

If you have not already done so, you need to flash the BIOS. Dell provide this on their support pages. It was an exe that you run under windows and it enabled WOL as it was not in the original 2007 version.

Sadly, if you have the RC410 [Radeon Xpress 200] on board it does not work correctly with the open source drivers.

I am having to use Unity-2d.

Hope this helps.

---

### Post by xorkid on 2011-08-03
Hi Mr-Badger,

Thanks for your reply, It has been a while!

I did update to the latest Dell BIOS. Still no luck with WOL though -  worked under windows, so my guess it was an ubuntu-related problem. Also it had an ATI graphics card, (not sure which one) built-in but I had no problems running it with 10.10 graphic effects. I no longer have it to check though.

Anyway the simplest solution I could find was to just buy a PCI WOL card on ebay for £2. Worth much less than the time I spent trying to fix it!

Thanks for your help though :-)

---

