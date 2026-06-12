---
title: "How to find out the reason for system freezes?"
date: 2006-01-14
forum: General Help
---

### Post by didi156 on 2006-01-14
I'm running Ubuntu on a Thinkpad T23.
Sadly it's not running very stable, it happens that the whole system freezes. With freeze I mean that there is no way to get some reaction from the system. Frozen mouse pointer, frozen display content, no IDE activity, no reaction to any key combination (Ctrl-Alt-Backspace, Ctrl-Alt-Esc), no response to remote pings.
Initially I suspected the WLAN driver, but with the driver module not loaded it also happend. It happend with and without power supply, with and without heay load at the moment of death. Before I rebooted to post this, it happend while I was doing Java programming, while the system was in a very idle state (not even a music player running).
It doesn't happen very often, maybe every 10-20 hours it's running. Thus it's also difficult to see a pattern.

It may be related to ACPI. Sometimes when booting, it hangs when saying "Uncompressing kernel...". Also, the Breezy installer froze when not invoked with acpi off. I then manually remoed the acpi=off switch in the grub config.
Since I'm using my laptop in a very "portable" way, hibernation and suspend is absolutely a must for me. I maybe would even think about switching to Windows, if I can't get it stable in Linux, and that means a lot, it's now about half a year that I don't have Windows installed on that machine (and it's my only one...).

My problem is that I have no idea how to find the cause of my instabilities. Assumed, it's ACPI, than it should somehow be possible to find out which operation makes it freeze. In the system logs I couldn't find anything useful.
I'd be very happy if somebody can tell me something useful, maybe also give me a hint about problems specific to the T23, maybe tell me a distro which works well with this machine...

---

### Post by tassou on 2006-01-14
hi didi156,
I have been loging mailing lists for linux on thinkpad for the last 3 month and I can not see any problem about system freezes on the T23. So I would bet it is not specific. Also when using linux on thinkpad, the thinkwiki is a must : [http://www.thinkwiki.org/wiki/Category:T23](http://www.thinkwiki.org/wiki/Category:T23)

So do you use proprietary graphic drivers ?

Could you lauch a memtest (you will find it in grub) for at least 3 hours ?

Finally, I think that if your system hang without any output in the log, it is likely to be a hardware problem. So switching to windows would be sad and maybe useless.

paul

---

### Post by Leigh on 2006-01-14
Is it a temperature thing, I wonder. Does it hang after several hours of use, indicating that something has heated up sufficiently to cause a breakage in the circuitry, e.g. dry solder joint.

Has it ever worked successfully, again I'm wondering if it's a corrupt install of Linux or associated drivers. Have you tried a clean reinstall?

---

### Post by BathroomNinja on 2006-01-14
I always test these things with the Live CD.  boot to the live CD, use the 'acpi=off' setting, let it sit for the time period that it normally takes.  If it doesn't lock up on you, then let it keep going for much longer.  This is a good way to see if the problem is software or hardware specific.  If it still locks up, it's probably an issue with the hardware, if not, it's probably an issue with ubuntu.

---

