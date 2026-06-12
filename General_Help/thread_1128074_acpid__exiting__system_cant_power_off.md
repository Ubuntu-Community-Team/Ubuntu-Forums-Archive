---
title: "acpid : exiting : system cant power off"
date: 2009-04-17
forum: General Help
---

### Post by Wodenberg on 2009-04-17
Hello !
A little problem with Intrepid, apparently well known on forums but with no answer or great solution for me.
My system can not power off.

To resume, after a logo-progression bar showing us powering-off, I have a black screen with message "acpid : exiting".

Solutions are proposed on forums :
-to add a line "ifconfig wlan0 down" in file /etc/init.d/alsa-utils, apparently a problem with alsa-network -> no effect
-to use magic keys to close applications, hard drives and reboot the pc : it does not close my HDD and just reboot, I want to power off...
-to use a shutdown command, or to add acpi=force, but it does not solve my problem.

The only solution I have to power off is to push off-button, not very good for HDDs.

After some tries I seen many messages while trying to close the system :
"* killing all remaining processes [fail]"
"mount : / is busy"
"the system is going down for reboot now"
but after these the system freezes

Under Hardy I could hear my HDD stopping, but with Intrepid they still run.

Thanks for help ;)

---

