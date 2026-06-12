---
title: "Interesting dist-upgrade experience"
date: 2023-08-07
forum: Desktop Environments
---

### Post by DigiAngel on 2023-08-07
So...I have 2 older iMacs that both have 22 installed.  Probably 22.0....maybe 1 or 2?  Not sure.  In any case, my update process is apt update, apt dist-upgrade.  On both of these iMacs, after doing apt dist-upgrade, both rebooted to a login console.  I had to do an apt install ubuntu-desktop to get back to Xwindows and gdm.  Just an FYI really.

---

### Post by Holger_Gehrke on 2023-08-07
That's either 22.04 or 22.10. Ubuntu version numbers are release dates, a new release is published every April and October. The release published in April of even numbered years is a Long Term Support release, which is what users who don't want or need to be on the bleeding edge should use.

'apt dist-upgrade' is the slightly more dangerous form of 'apt upgrade' in the sense that 'upgrade' will never install new packages, even if an upgraded package has changed dependencies which make installing a new package necessary. If that happens, 'upgrade' will not change the package while 'dist-upgrade' will and will also install the new dependency.

'ubuntu-desktop' is a package that contains almost nothing - I think it's just a few 'Readme'-files in /usr/share/docs. Everything is done through dependencies and recommendations. There's about 50 packages it depends upon and more than a hundred it recommends. If you removed any of the dependencies, then the ubuntu-desktop package breaks and is removed which will then trigger the removal of all it's dependencies and recommendations which aren't necessary for something else. So either somebody made a big error setting up some updated packages which conflicted with the desktop - in which case we will soon be up to our ears in posts about this - or you removed something you didn't know was important.

Holger

---

### Post by ian-weisser on 2023-08-07
There were several similar reports over the weekend.

In the sole case I've seen where somebody did troubleshooting, they quickly discovered that Phased Updates was holding back parts of the 22.04.3 release.

---

