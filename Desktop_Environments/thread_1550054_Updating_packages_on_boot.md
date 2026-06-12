---
title: "Updating packages on boot"
date: 2010-08-10
forum: Desktop Environments
---

### Post by StealthCP on 2010-08-10
So I decide to start posting here.  First I'll explain the situation.

A Workstation in a University dual-boots Win7 and UbuntuLTS.  Both (will) authenticate users on Active Directory.  There is a web-server on site, which contains a repository, containing private packages involving scripts and data, all keeping everything running smoothly.

It is important Ubuntu gets package updates (for everything) before the system is fully booted up.  I mean on EVERY boot.  The desirable option would be to have the system grab an IP via DHCP first thing on boot (any other required services for networking only), upgrade all packages on the system (if available), then continue booting.

To clarify:  I would like the system to receive package upgrades on boot before the system is fully up, and to wait until package upgrades are done before continuing to boot the system.

Can this be done?

---

### Post by StealthCP on 2010-08-17
Any ideas on this?

I'm now reckoning the best way to go about this is writing a script in bash that will run on startup, check for networking and perform package upgrades, etc.  Can anyone give me tips on examples that this script needs to perform, and the best place to store the script?  (It will be later placed in a package so that changes can be made to it, and installed by default upon setting up the system initially)

---

