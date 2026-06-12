---
title: "VNC vs X11 for remote desktop over WiFi"
date: 2019-06-28
forum: Desktop Environments
---

### Post by porton2 on 2019-06-28
I want to access my PC from my laptop. Use VNC or ssh -X (-Y)? I want fullscreen (or a big window) for the PC control on the laptop.

BTW, what is the difference between ssh -X and ssh -Y?

WiFi, Gnome, Ubuntu 19.04 Desktop on both machines.

---

### Post by cmcanulty on 2019-06-28
for dead simple try anydesk

[https://anydesk.com/en/downloads/linux]("https://anydesk.com/en/downloads/linux")

---

### Post by TheFu on 2019-06-28
No full desktop will work with gnome3 very well, if at all.  You can use gnome2, LXQt, LXDE, or any of the lighter window managers.  Gnome3 is NOT light and I believe there is only 1 possible solution, but it doesn't work. It is from the [gnome project]("https://wiki.gnome.org/Projects/Mutter/RemoteDesktop").   

-X and -Y have different security considerations.  -Y isn't as secure. Check the ssh manpage for the exact differences.  That is an important skill.

If you want a full desktop, I would encourage you to check out x2go.  It feels 2-3x faster than VNC or RDP. It uses the NX protocol which uses ssh for authentication and tunnelling. That makes it 1000x more secure than VNC's zero security or RDP's broken security.  I've posted short instructions in these forums for x2go in the last few weeks.

If you are running the desktop inside a KVM virtual machine, then there is a faster choice - use SPICE.  SPICE is pretty awesome, but it isn't a generic solution without the kvm hypervisor.

Poor wifi networking will be an issue with any network protocol. Wifi seems fine to humans surfing and checking email, but when data-heavy protocols are used, how poor a wifi connection really is becomes clear. 

I see you are using 19.04.  If you are really new to Linux then I would encourage you to load the current LTS release, 18.04.  Support for 19.04 ends in December _this_ year. Only LTS releases have 5 yrs of support. All the others get 9 months from their release date.

---

### Post by TheFu on 2019-06-28
> **cmcanulty said:**
> for dead simple try anydesk

[https://anydesk.com/en/downloads/linux]("https://anydesk.com/en/downloads/linux")

$11/month, not including VAT and that is for 1 device. Think that was an important detail worth mentioning?

---

