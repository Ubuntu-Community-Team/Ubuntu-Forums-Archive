---
title: "LVM startup problem after 9.04 upgrade"
date: 2009-05-10
forum: General Help
---

### Post by TheBigAmbulance on 2009-05-10
Hey All,

I was wondering if you could please help me out.  I had a LVM for storage that worked fine under 8.10.  After performing an upgrade to 9.04, my LVM init script no longer worked.

I've used the script here for quite some time:
_*[U]**[http://www.tldp.org/HOWTO/LVM-HOWTO/initscriptdebian.html](http://www.tldp.org/HOWTO/LVM-HOWTO/initscriptdebian.html)**_*[/U]

Thinking that it might have been something borked with the current install, I backed everything up and did a fresh install of 9.04 and then install lvm2.  The script would still not work on reboot.  The LVM still exists and works if I manually 'vgscan', 'vgchange -ay' and 'mount' the LVM.  The startup script in /etc/init.d/lvm will not function any longer.

I've tried searching for bugs on this topic, but have not been able to find anything.

Thanks for any help or pointers you can give on this topic!

---

