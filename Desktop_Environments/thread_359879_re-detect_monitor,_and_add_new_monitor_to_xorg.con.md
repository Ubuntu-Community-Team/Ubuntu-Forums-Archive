---
title: "re-detect monitor, and add new monitor to xorg.conf"
date: 2007-02-12
forum: Desktop Environments
---

### Post by loonsailor on 2007-02-12
I just got a nice new NEC monitor, and I'm having a problem with resolution.  I have the ubuntu (Dapper) box plugged into the analog port (via a kvm), but the monitor is usually switched to a digital port and my MacPro.  If the monitor is switched to the ubuntu when it reboots, all is good, but it the monitor is switched away (as is usual) when the ubuntu reboots, when I do switch the monitor to it the resolution is stuck at 640x480, and there are no other options in the gnome display res. applet.  I assume that it isn't finding a monitor when it reboots, and therefore its defaulting to the low res.  Is there anything I can do other than rebooting the system at that point?  Is there a way to make X re-detect the monitor, or to default to a higher res?

Also, in looking at my xorg.conf, the monitor listed is an old one.  Do I need to make a new monitor section, and if so, is there a tool to use or do I just vi xorg.conf directly?

Thanks for any help.

---

### Post by dcstar on 2007-02-12
> **loonsailor said:**
> I just got a nice new NEC monitor, and I'm having a problem with resolution.  I have the ubuntu (Dapper) box plugged into the analog port (via a kvm), but the monitor is usually switched to a digital port and my MacPro.  If the monitor is switched to the ubuntu when it reboots, all is good, but it the monitor is switched away (as is usual) when the ubuntu reboots, when I do switch the monitor to it the resolution is stuck at 640x480, and there are no other options in the gnome display res. applet.  I assume that it isn't finding a monitor when it reboots, and therefore its defaulting to the low res.  Is there anything I can do other than rebooting the system at that point?  Is there a way to make X re-detect the monitor, or to default to a higher res?

Also, in looking at my xorg.conf, the monitor listed is an old one.  Do I need to make a new monitor section, and if so, is there a tool to use or do I just vi xorg.conf directly?

Thanks for any help.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by loonsailor on 2007-02-13
Thanks for the help, David.  Actually, that created an xorg.cong that won't let X run, but it is still helpful and I'll figure it out.

It doesn't help me with the main problem, though.  When the computer boots "headless", how do I make it detect a monitor properly when I plug it in later, short of a reboot?  Do I need to restart X (how?), or is there a kill signal (which one?) or is there some command that I issue to X?

Thanks.

---

### Post by dcstar on 2007-02-13
> **loonsailor said:**
> Thanks for the help, David.  Actually, that created an xorg.cong that won't let X run, but it is still helpful and I'll figure it out.

It doesn't help me with the main problem, though.  When the computer boots "headless", how do I make it detect a monitor properly when I plug it in later, short of a reboot?  Do I need to restart X (how?), or is there a kill signal (which one?) or is there some command that I issue to X?

Thanks.

```
sudo /etc/init.d/gdm restart
```

There is also a command option for the dpkg-reconfigure xserver-xorg that will auto-accept all detected hardware (like the live CD does), but I can't remember where in the forums I saw it recently.

---

