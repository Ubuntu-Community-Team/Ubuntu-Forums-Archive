---
title: "sauerbraten uninstalled on update."
date: 2008-07-26
forum: Gaming &amp; Leisure
---

### Post by sparky64 on 2008-07-26
Hi.
Did an autoupdate this morning and noticed sauerbraten had uninstalled.
I tried reinstalling from synapaptic but get the message "depends on sauerbraten data but will not be installed.
when i try via apt i get.

"The following packages have unmet dependencies.
  sauerbraten: Depends: sauerbraten-data (>= 0.0.20080620-1) but it is not going to be installed
E: Broken packages"

sauerbraten-data is still installed on my system and has updated to the latest version.
I am running heron with the latest nvidia drivers and was playing it fine last night.
I have also tried fixing broken packages but get the message "no broken packages" ?
I am downloading the game from the main site looking to compile it from scratch, But am unsure if it will stuff my system.

Any help will be much appreciated.
Sparky64

---

### Post by angryfirelord on 2008-07-27
Same here. It seems that whoever packaged the sauerbraten update didn't inspect their work. The problem is that the sauerbraten package depends on sauerbraten-data 0.0.20080620-1, but instead the repositories have sauerbraten-data 0.0.20080620-1~hardy1. Therefore, when apt looks at this, it counts it as a missing dependency because the version numbers don't line up.

The bug report is here: [https://bugs.launchpad.net/ubuntu/+source/sauerbraten/+bug/252037]("https://bugs.launchpad.net/ubuntu/+source/sauerbraten/+bug/252037")

---

