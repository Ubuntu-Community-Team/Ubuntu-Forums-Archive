---
title: "Broadcom wireless fails on Jaunty kernel update"
date: 2009-11-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mirach on 2009-11-30
I have a mini 9 and did a clean install of 9.04-lpia. The Broadcom wireless worked fine and if I look under Admin > Hardware Drivers I see the proprietary Broadcom STA wireless Driver is activated.

Unfortunately after updating (2.6.28-11-lpia went to 2.6.28-16-lpia) the card is no longer recognised (under Admin > Hardware Drivers it's blank).

Booting back into 2.6.28-11-lpia everything's fine again. Any idea how to fix it?

Thanks,

P.S. I've tried Karmic and it works great but I can't handle the long boot time with the mini 9.

---

### Post by superm1 on 2009-12-01
Sounds like you're missing the headers for that kernel.  Look around for a metapackage for them to make sure they get installed with all kernel updates.

---

### Post by mirach on 2009-12-02
Thanks for the reply - Here are some more details:


After a clean install of 9.04 lpia wireless is working.

If I go to upgrades I get an upgrade message that says this:

	Not all updates can be installed

	Run a partial upgrade, to install as many updates as possible.

	This can be caused by:

	> A previous upgrade which didn't complete
	> Problems with some of the installed software
	> Unofficial software packages not provided by Ubuntu
	> Normal changes of a pre-release version of Ubuntu


When I click the Partial Upgrade button it tells me it's going to do the following:

	Remove linux-lpia
	install linux-headers-2.6.28-16
	install linux-headers-2.6.28-16-lpia
	install linux-image-2.6.28-16-lpia
	Upgrade linux-headers-lpia
	Upgrade linux-image-lpia


After doing this and rebooting the Broadcom wireless stops working.


If I then go into synaptic and do "Status > Installed (Upgradable)" it shows that:

	linux-restricted-modules-lpia is still at version 2.6.28.11.15

If I mark it for upgrade I get the following error message:

	Could not mark all packages for installation or upgrade

	The following packages have unresovable dependencies.
	Make sure that all required repositories are added and enabled in the preferences.

		linux-restricted-modules-lpia:
		 Depends: linux-restricted-modules-2.6.28-16-lpia  but it is not installable

Thanks again...

---

