---
title: "moving /var off of compact flash drive"
date: 2009-01-23
forum: General Help
---

### Post by RaygionsSumta on 2009-01-23
I have installed 8.10 to a compact flash card  and wish to move /var and ./tmp off of the CF card and onto the existing software RAID in that box.  My approach was to:

[LIST]
[*]cp -ax  /var /raid
[*]boot into live CD (the original /var  was still locked in ‘init 1’)
[*]cp var var.old
[*]rm -Rf var
[*]ln -s /raid/var /var
[*]reboot into the OS
[/LIST]

The symbolic link did not seem to be recognized when I rebooted.  Thoughts?

---

