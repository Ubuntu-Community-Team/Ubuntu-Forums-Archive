---
title: "do I need these services (avahi, wpa-ifupdown, portmap, udev and others)"
date: 2009-05-15
forum: General Help
---

### Post by mrowth on 2009-05-15
I doubt most of these services eat much CPU or RAM, but it annoys me to have no real idea what something actually is or does. 

So here I am with sysv-rc-config in a console.

quota, quotarpc: As in disk quotas? Do I need that as a home user? 

rmnologin:  I've read that "rmnologin prevents non-root users from logging in", but I **only** log in as a non-root user. ?

loopback: This isn't in init.d, but sysv-rc-conf shows it (as not starting in any runlevel). ifconfig status shows the "lo" interface.

winbind: Without Windows domains, do I need winbind? (Installed as a package? Running as a service?)

acpid: Only difference I notice with this running is this: It overrides KDE 4's shutdown dialog with an abrupt "shutdown -h now". So is there any reason to keep it? Seems I can suspend to RAM without it. Normally. (And I can't hibernate either way.)

acpi-support: Not a laptop, any reason to keep it? 

portmap: I just read this was for NFS. But I dimly recall dealing with a portmapper while setting up a local Postifx ages ago. portmap is thus necessary for _______?

udev, udev-finish: There's a udevd processes running, but these services aren't enabled in any runlevel. Is that bad? Is upstart running it?

avahi-daemon: Superunknown to me and I'm not sure under what circumstances which apps would take advantage of this in what way. 

saned: Seems this would make scanners available on the network, presumably in cooperation with avahi-daemon? (Would xsane on another PC on the LAN then offer my local scanner?)

wpa-ifupdown: I have no idea what this does, except it has to do with wireless. If I ditch the annoying cables, will I need this? Will I need this and NetworkManager? Seems KDE 4 users are generally recommended to use wicd instead of NetworkManager. I don't use NetworkManager for wired connections either.

stop-bootlog: What's the difference between (1) **stopping** bootlogd in a runlevel, and (2) **starting** stop-bootlogd? I suppose since there's no Kxxbootlogd script in (say) rc1.d, it's the ...well, there's no Sxxstop-bootlogd either! There's a S70bootlogs.sh though.

---

### Post by evermooingcow on 2009-05-15
For comparison I don't have the below services running on my system and it seems to be doing fine without them.

quota
winbind
acpi-support
portmap (exists but not running)
avahi
saned
wpa-ifupdown

---

### Post by mrowth on 2009-05-15
> **evermooingcow said:**
> For comparison I don't have the below services running on my system and it seems to be doing fine without them.

quota
winbind
acpi-support
portmap (exists but not running)
avahi
saned
wpa-ifupdown

Hmm. Are you using WLAN? NetworkManager? wicd? 

(What about quotarpc?)

What about bootlogd, stop-bootlogd and stop-bootlogd-single? I overlooked something but I'm still puzzled:

rcS.d: 
S20bootlogd --> starts bootlogd
S20stop-bootlogd-single --> starts stop-bootlogd-single

rc1.d:
K80bootlogd --> stops bootlogd

rc2.d:
K80bootlogd --> stops bootlogd
S20stop-bootlogd --> starts stop-bootlogd 

File /var/log/boot says nothing's been logged yet. And it's over 10 months old.

Is there a (safe & ideally simple) way to clean out stuff that doesn't even exist on my system but still shows up in runlevel editors (e.g. bootchart, acpi-support, usplash...)? 

Is there a way to NOT try to stop services that weren't running in the first place, short of manually deleting the links in the rc*.d directories? (e.g. no "Stopping winbind daemon" etc. when there's never been a winbind daemon running...)

---

