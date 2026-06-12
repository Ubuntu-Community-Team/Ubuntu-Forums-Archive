---
title: "Rogue eth0 after Firefox crash"
date: 2008-12-30
forum: General Help
---

### Post by bcschmerker on 2008-12-30
I occasionally have Mozilla Firefox 2.0.0.19 (the latest version available for Ubuntu 7.10-back) crash, mid-page load, with exit code 130 or 139, and find, via System Monitor, that /dev/eth0 is constantly transmitting, jamming my house's router.  This problem is recurring, usually in relation to a detected JS leak.  System Monitor doesn't give me the data I need to stop the rogue transmit commands (other than pulling /dev/eth0 offline).  Which modules and/or drivers would be involved in this problem, which starts when a JavaScript process in Firefox is still held in native code after a tab or window is closed?  (Leak Monitor 0.3.6 tips me off to the still-unidentified start of the rogue-Ethernet-adapter situation.)

---

### Post by Sin@Sin-Sacrifice on 2008-12-30
Have you tried different version of java?

---

### Post by bcschmerker on 2008-12-31
> **Sin@Sin-Sacrifice said:**
> Have you tried different version of java?

I don't believe Java to be a factor in this case.  There have been earlier threads on Bugzilla.Mozilla.org about memory leaks in some LinUX builds of Firefox 2 under a wide variety of installation conditions, both with and sans Sun Microsystems' Java Runtime Environment; besides, on my last attempt to install the Java plugin, to my chagrin Sun Microsystems didn't have a Debian version of Java Runtime Environment 6 (I've had no consistency to date with Red Hat RPM).

---

### Post by bcschmerker on 2009-01-07
> **bcschmerker said:**
> I don't believe Java to be a factor in this case.  There have been earlier threads on Bugzilla.Mozilla.org about memory leaks in some LinUX builds of Firefox 2 under a wide variety of installation conditions, both with and sans Sun Microsystems' Java Runtime Environment; besides, on my last attempt to install the Java plugin, to my chagrin Sun Microsystems didn't have a Debian version of Java Runtime Environment 6 (I've had no consistency to date with Red Hat RPM).

Update:  The problem occurs even with a fully functional Java Runtime Environment 6, so the problem definitely involves Firefox and at least one of the daemons with whom Firefox has to interact to reach the Web.

---

### Post by bcschmerker on 2009-03-21
Ha...should've read the docs!  It turned out to be the ntp package, as /sbin/ntpd was attempting to synchronize with the network from a client port; the Netgear WGR614v5 that I had at the time couldn't hack it, and I don't believe the Linksys/Cisco WRT400N would have necessarily done any better (as the rogue /dev/eth0 condition had characteristics consistent with a Denial of Service attack).

(The Everex has since had not only the ntp package purged but also an AMD/nVIDIA system board substituted for the all-VIA system board whereon the trouble occurred.)

---

### Post by bcschmerker on 2009-05-19
> **bcschmerker said:**
> ...It turned out to be the ntp package, as /sbin/ntpd was attempting to synchronize with the network from a client port; the Netgear WGR614v5 that I had at the time couldn't hack it, and I don't believe the Linksys/Cisco WRT400N would have necessarily done any better (as the rogue /dev/eth0 condition had characteristics consistent with a Denial of Service attack)....)Beware of overzealous use of the Network Time Protocol Daemon, /sbin/ntpd (Pakage: ntp), as this Daemon will jam routers in residential broadband installations, a problem I discovered firsthand with the Netgear WGR614v5 (prob. applies to later submodels).  The Package ntp-doc includes extensive HTML documentation of this Daemon, configuration rules and syntax, etc. necessary for reliable and interference-free operation.):P

---

