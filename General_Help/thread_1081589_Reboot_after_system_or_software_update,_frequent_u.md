---
title: "Reboot after system or software update, frequent under Linux?"
date: 2009-02-26
forum: General Help
---

### Post by UranUtan on 2009-02-26
Hi,

This is not a troll to flame Linux. I have heard that Linux doesn't require reboot often like Windows does.

When I do system update and sometime software update (like updating VirtualBox Guest Additions). There is a prompt to ask for reboot.

I don't mind rebooting at all. But what is exactly the "myth" behind the reboot of a Linux system?

---

### Post by bodhi.zazen on 2009-02-26
The only time you really need to reboot is to boot a new kernel, and we are working on that ...

Otherwise you almost never need to reboot.

---

### Post by Slim Odds on 2009-02-26
> **UranUtan said:**
> Hi,

This is not a troll to flame Linux. I have heard that Linux doesn't require reboot often like Windows does.

When I do system update and sometime software update (like updating VirtualBox Guest Additions). There is a prompt to ask for reboot.

I don't mind rebooting at all. But what is exactly the "myth" behind the reboot of a Linux system?

Well, the only time linux "really" needs to reboot is for a kernel update. But, sometimes people just take the easy way out when something like a kernel module needs to be updated.

Because there are dependencies, it's sometimes a very difficult thing to unload and reload all of the correct modules.

VirtualBox Guest Additions is a bit of a special case. Since you're only rebooting a virtual OS.

(LOL, me and Bo are bros)

---

### Post by ryan.nabinger on 2009-02-26
to add as a flaming troll:

Windows needs to be rebooted all the time because it is plagued with memory leaks and poor design which decreases performance and stability with uptime.

---

