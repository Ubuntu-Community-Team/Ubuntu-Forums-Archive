---
title: "Breezy boot pauses on Loading Modules"
date: 2006-01-04
forum: General Help
---

### Post by le_jawa on 2006-01-04
Hello all!

I've just got a small one for y'all.  I've installed Breezy on a couple of different PC's and have run into an annoyance on my desktop.  When the system starts, the splash screen sits several seconds (15 - 20), then reverts to the text messages from the boot process, where it sits several more seconds (about the same delay) on the message "Loading modules".  Does anyone know what causes this and what can be done to resolve it?  It's not a huge deal, but a solution would be nice.

Thanks everyone!

---

### Post by dcstar on 2006-01-04
[QUOTE=le_jawa]Hello all!


I've just got a small one for y'all.  I've installed Breezy on a couple of different PC's and have run into an annoyance on my desktop.  When the system starts, the splash screen sits several seconds (15 - 20), then reverts to the text messages from the boot process, where it sits several more seconds (about the same delay) on the message "Loading modules".  Does anyone know what causes this and what can be done to resolve it?  It's not a huge deal, but a solution would be nice.

Thanks everyone![/QUOTE]
It may be timing out on a module which cannot load on your PC.

Change /etc/default/bootlogd to "Yes" and you should get a /var/log/boot file to look at for any error messages.

Also change /etc/default/rcS to "VERBOSE=yes" for more info during the boot process.

If you find the bad module, you should be able to stop it loading.

---

### Post by le_jawa on 2006-01-04
Heck of a good idea, but I ran into another snag: bootlogd refuses to start.  I get a message back saying "bootlogd: cannot find console device 136:0 in /dev".  I googled for it and found that this was once caused by a bug in udev, and that having bootlogd load before udev in the startup scripts was the fix. 

Well, that bug was for a much older version of udev than Breezy uses, and changing the order did nothing.  Does anyone know a fix for this?

Thanks again for the help.

(Edited)
Let me add a little info here, and correct my earlier comment.  On the splash screen I get the message "Loading modules, and it sits there for 10-15 seconds with no drive activity.  The the splash screen clears and the regular text screen shows, with the last message being "Loading, please wait..." preceded by kernel information.  Evidently, the problem is, as dcstar pointed out, a kernel or module issue.  I checked the kernel log, and found a delay on each boot of 20 - 22 seconds, and the first message in the delay is for bluetooth modules, and my PC doesn't have bluetooth.  Maybe that's it, but my laptop doesn't have bluetooth either, and it doesn't do this.  I also noticed the kernel saying there were no symbols for modules, but I'm reasonably certain that Ubuntu does use modules, so I don't get that at all (I'm no guru at the kernel...).

Anyway, here are the the entries I'm referring to:
[FONT=Courier New] Jan  4 21:49:31 localhost kernel: Inspecting  /boot/System.map-2.6.12-9-386
Jan  4 21:49:31 localhost kernel: Loaded 29002 symbols from /boot/System.map-2.6.12-9-386.
Jan  4 21:49:31 localhost kernel: Symbols match kernel version 2.6.12.
[COLOR=Blue] Jan  4 21:49:31 localhost kernel: No module symbols loaded - kernel modules not enabled. [/COLOR]
Jan  4 21:49:31 localhost kernel: .296000] Console: colour VGA+ 80x25
[FONT=Verdana]There's one of the lines that concerns me, but maybe that's normal; I really don't know.  You can see from the line after it anyway that there's no delay.

The delay is here:
[FONT=Courier New]Jan  4 21:46:44 localhost kernel: [4294730.209000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jan  4 21:46:44 localhost kernel: [4294730.209000] apm: overridden by ACPI.
[COLOR=Red]Jan  4 21:46:45 localhost kernel: [4294730.739000] eth0: no IPv6 routers present
Jan  4 21:47:07 localhost kernel: [4294752.750000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)[/COLOR]
Jan  4 21:47:07 localhost kernel: [4294752.750000] apm: disabled on user request.
Jan  4 21:47:10 localhost kernel: [4294755.996000] Bluetooth: Core ver 2.7
Jan  4 21:47:10 localhost kernel: [4294755.996000] NET: Registered protocol family 31
Jan  4 21:47:10 localhost kernel: [4294755.996000] Bluetooth: HCI device and connection manager initialized[/FONT]

The IPV6 router entry seems to move around in the log (and sometimes is not particularly close to the delay), but the rest seems pretty consistent.  If anyone can make better sense of this and provide a solution, I would appreciate it.  (End edit)
[/FONT][/FONT]

---

### Post by gaspedalo on 2006-02-19
Hi!
I got similar problems. I trie to enable bootlog, but it says bootlogd failed. I got a /var/boot file, but it seems to have started the second after the waiting on the modules. So I#m pretty stuck in here. The only detail I can add is that I found my CDRom Drive Light lit during the waiting process. When the machine eventually starts booting the light's off. Does that give you ideas?

---

