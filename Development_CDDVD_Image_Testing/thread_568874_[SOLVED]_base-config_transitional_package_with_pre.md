---
title: "[SOLVED] base-config transitional package with preseed problems"
date: 2007-10-06
forum: Development CD/DVD Image Testing
---

### Post by BrandonPerry on 2007-10-06
Hi, there seems to be posts all over the forum about base-config not working properly, yet no answer has been found (or posted) for a problem like mine. I am trying to start a ClamAV virus scan as soon as the cd boots up, but it never starts it, it just boots up normally. I replaced the ClamAV line with 

base-config base-config/late_command string reboot

and it still does nothing. This is really bugging me as I have been working on it for about 2 weeks now with now answer,

Here is my preseed file stub:

# Only install the standard system and language packs.
tasksel	tasksel/first	multiselect
d-i	pkgsel/language-pack-patterns	string
# No language support packages.
d-i	pkgsel/install-language-support	boolean false
#this should be
#base-config base-config/late_command string bash /opt/virus_scan.sh
base-config base-config/late_command string reboot

That does nothing, It just boots and sits there,
Here is the isoconfig lines for it:

LABEL clamav
  menu label Start A ClamAV ^Virus Scan
  kernel /casper/vmlinuz
  append file=/cdrom/preseed/clamav.seed boot=casper initrd=/casper/initrd.gz nosplash -- 

Any help is greatly appreciated...

---

