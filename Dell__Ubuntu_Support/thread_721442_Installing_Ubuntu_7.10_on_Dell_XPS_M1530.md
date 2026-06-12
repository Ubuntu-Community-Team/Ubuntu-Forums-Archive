---
title: "Installing Ubuntu 7.10 on Dell XPS M1530"
date: 2008-03-11
forum: Dell  Ubuntu Support
---

### Post by gecko113 on 2008-03-11
Has any one figured out how to get the figure print reader working and also the mic working i've tried serveral times to fix it but no use. Also do u kno about any drivers that are out for ubuntu at the current momment for the xps m1530

---

### Post by damis648 on 2008-04-20
I also have an M1530, and this stuff is quite easy to fix. For the internal mic, just execute the commands given on this page: [http://weblogs.inf.udp.cl/nboettcher/28/02/2008/configurar-microfono-en-ubuntu-gnome-en-equipo-dell-xps-m1330-m1530/](http://weblogs.inf.udp.cl/nboettcher/28/02/2008/configurar-microfono-en-ubuntu-gnome-en-equipo-dell-xps-m1330-m1530/)
and after you reboot double click the volume icon in the panel and goto Edit>preferences and add the tracks Surround, Digital and Digital Input Source and click close. Increase the Master and Surround in the playback tab. Then just Increase the Digital level under the Recording tab. Select Digital Mic 1 for the Digital Input Source under the Options tab. NOTE: Make sure nothing is muted under the levels.

And you should be good to go! :)

As for the fingerprint reader, just visit [http://thinkfinger.sourceforge.net/](http://thinkfinger.sourceforge.net/) and follow the directions on the site.

Credits to LukasD for the internal mic problem.

---

### Post by master_kernel on 2008-04-20
Also try fprint: [http://ubuntuforums.org/showthread.php?t=760018](http://ubuntuforums.org/showthread.php?t=760018)

---

