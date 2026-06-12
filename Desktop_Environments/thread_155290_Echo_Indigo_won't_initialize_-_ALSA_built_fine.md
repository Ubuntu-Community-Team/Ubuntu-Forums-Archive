---
title: "Echo Indigo won't initialize - ALSA built fine"
date: 2006-04-04
forum: Desktop Environments
---

### Post by onyxrev on 2006-04-04
Hey!  Brand new here... been running Dapper and 2.6.15-19-k7 on my Gateway MX7515 for a while now and really dig it.

I have an Echo Indigo (not the I/O version) and am interested in getting it working with my laptop.  It's installed in the PCMCIA slot.  I've followed the directions in the ALSA source - /usr/share/doc/alsa-base/README.Debian and everything built just fine.  When I modprobe the drivers into the kernel as per [ALSA's instructions]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Echo+Digital+Audio+Corporation&card=Indigo.&chip=Motorola+56361&module=indigo") I get no errors but the card doesn't light up with the ubiquitous blue light and isn't present in the ALSA mixer.  I figured maybe the card isn't hotplugable so I tried a reboot with the card installed but that didn't make a difference.

The built in Conexant sound works great with the new ALSA modules.

Any thoughts?  Thanks!

---

