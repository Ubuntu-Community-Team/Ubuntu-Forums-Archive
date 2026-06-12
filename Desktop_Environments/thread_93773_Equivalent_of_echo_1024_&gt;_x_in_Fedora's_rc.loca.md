---
title: "Equivalent of echo 1024 &gt; x in Fedora's rc.local"
date: 2005-11-22
forum: Desktop Environments
---

### Post by ultranet on 2005-11-22
I've used 
dev.rtc.max-user-freq=1024
in /etc/sysctl.conf
but after reboot, the value in /proc/sys/dev/rtc/max-user-freq is still 64.

rc.local is the last script ran in Red Hat. What is the last script in Ubuntu/Debian?

P.S. Also wonder about the first one, which i think is rc.sysinit in Red Hat.
P.P.S. Also if anybody encountered mpayer frame not resizing with the window size, i'd appreciate your feedback. I built it from source. Synaptic URLs weren't correct, and i think they wouldn't come with gmplayer (gtk).
P.P.P.S. Also, what is the equivalent of
rpm -qa | grep kernel
in Ubuntu (using dpkg i guess)?

Thanks.

---

