---
title: "Unknown program always still running at logout"
date: 2008-12-26
forum: General Help
---

### Post by ricardisimo on 2008-12-26
This is always on the main user account on my work comp, and only that account. On the others, "Tomboy still running" will briefly flash onscreen, then disappear and logout continues.

Why would the system not know what is running? That's a little disturbing. Any ideas how to dissect this? Thanks in advance.

---

### Post by hxcgrunger on 2008-12-28
Do you by any chance have: "http://projects.gnome.org/tomboy/" installed?

---

### Post by ricardisimo on 2008-12-29
Yes, I have Tomboy installed, and as I mentioned, tomboy is a tad slow to shut down at logout, but it flashes for only a second, then it's gone. "unknown program," however, never shuts down. I always have to select "Logout anyway."

---

### Post by dcstar on 2008-12-29
> **ricardisimo said:**
> Yes, I have Tomboy installed, and as I mentioned, tomboy is a tad slow to shut down at logout, but it flashes for only a second, then it's gone. "unknown program," however, never shuts down. I always have to select "Logout anyway."

It probably means that you uninstalled something that did not clean itself up correctly, look in your /etc/rc0.d for something that should not be there.

---

### Post by ricardisimo on 2008-12-30
My limited knowledge would tell me nothing regarding what should or should not be there. Does anything here strike you as odd:
[INDENT]/etc/rc0.d/K01gdm
/etc/rc0.d/K01timidity
/etc/rc0.d/K02usplash
/etc/rc0.d/K16dhcdbd
/etc/rc0.d/K20apport
/etc/rc0.d/K20dkms_autoinstaller
/etc/rc0.d/K20libchipcard-tools
/etc/rc0.d/K20winbind
/etc/rc0.d/K25hwclock.sh
/etc/rc0.d/K39ufw
/etc/rc0.d/K50alsa-utils
/etc/rc0.d/K59mountoverflowtmp
/etc/rc0.d/K86avahi-daemon
/etc/rc0.d/K99laptop-mode
/etc/rc0.d/README
/etc/rc0.d/S01linux-restricted-modules-common
/etc/rc0.d/S15wpa-ifupdown
/etc/rc0.d/S20sendsigs
/etc/rc0.d/S30urandom
/etc/rc0.d/S31umountnfs.sh
/etc/rc0.d/S40umountfs
/etc/rc0.d/S60umountroot
/etc/rc0.d/S90halt[/INDENT]
Thanks.

---

### Post by ricardisimo on 2008-12-30
Hmmm... this is a desktop computer, so it is odd that I would have anything named "/etc/rc0.d/K99laptop-mode".

---

### Post by dcstar on 2008-12-30
> **ricardisimo said:**
> My limited knowledge would tell me nothing regarding what should or should not be there. Does anything here strike you as odd:
[INDENT]/etc/rc0.d/K01gdm
**/etc/rc0.d/K01timidity**
/etc/rc0.d/K02usplash
/etc/rc0.d/K16dhcdbd
**/etc/rc0.d/K20apport**
**/etc/rc0.d/K20dkms_autoinstaller**
**/etc/rc0.d/K20libchipcard-tools**
**/etc/rc0.d/K20winbind**
/etc/rc0.d/K25hwclock.sh
/etc/rc0.d/K39ufw
/etc/rc0.d/K50alsa-utils
/etc/rc0.d/K59mountoverflowtmp
/etc/rc0.d/K86avahi-daemon
/etc/rc0.d/K99laptop-mode
/etc/rc0.d/README
/etc/rc0.d/S01linux-restricted-modules-common
/etc/rc0.d/S15wpa-ifupdown
/etc/rc0.d/S20sendsigs
/etc/rc0.d/S30urandom
/etc/rc0.d/S31umountnfs.sh
/etc/rc0.d/S40umountfs
/etc/rc0.d/S60umountroot
/etc/rc0.d/S90halt[/INDENT]
Thanks.

The ones that I **don't** have in my 8.04 system are highlighted (but I don't have those packages installed).

---

### Post by Amitola85 on 2009-01-10
My laptop has the same problem in 8.10, I didn't have this problem in 8.04.  my rc0.d directory contains the following:
 
K01gdm
K02usplash
K16dhcdbd
K20apport
K20winbind
K25hwclock.sh
K39ufw
K50alsa-utils
K59mountoverflowtmp
K86avahi-daemon
K99laptop-mode
S01linux-restricted-modules-common
S15wpa-ifupdown
S20sendsigs
S30urandom
S31umountnfs.sh
S40umountfs
S60umountroot
S90halt

It's probably getting close to time to just do a clean install on this machine anyways.  I've installed/uninstalled all sorts of things over the years when messing with stuff.  But if anyone knows how to fix this problem without a clean install it'd be appreciated.

---

### Post by gmoctav on 2009-05-07
Now , I,ve got the same problem , on a laptop , with 9.04. I,ve tried to see the program with top , and to kill it , but it didn't work. Any ideea?

---

### Post by dagindiba on 2010-03-22
I have the same problem on Ubuntu 9.10. Two years later and no solution? (newb by the way)

---

