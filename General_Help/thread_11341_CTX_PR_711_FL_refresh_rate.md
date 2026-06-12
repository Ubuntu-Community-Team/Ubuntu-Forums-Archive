---
title: "CTX PR 711 FL refresh rate"
date: 2005-01-16
forum: General Help
---

### Post by pavkonti on 2005-01-16
i have CTX PR 711 FL and when I use 1152x864 my max refresh rate is 100Hz on my windows. when I use ubuntu my max refresh rate is 85 Hz.

My monitor is: [http://www.ctx.eactive.pl/futura.php?model=pr711fl](http://www.ctx.eactive.pl/futura.php?model=pr711fl)
I attached my XF86Config-4 file.

---

### Post by daniels on 2005-01-16
Remove the HorizSync and VertRefresh lines.

---

### Post by pavkonti on 2005-01-16
I removed the lines, but this did not help. My max refresh rate for this resolution is still 85 Hz

---

### Post by daniels on 2005-01-16
I don't know, you might need to Google for the proper sync rates for your monitor. It seems it's not advertising the ones it can actually do.

---

### Post by pavkonti on 2005-01-16
this is taken from suse 9.2 gnome live cd. I tried to copy and paste the sections monitor, modes, device and sreen, but I received some error, when I restarted gnome.

---

### Post by pavkonti on 2005-01-24
is it possible somewhere(in config files) to be set max refresh rate 85Hz, because max refresh rate is 85Hz of all my resolutions? :neutral:

---

### Post by pavkonti on 2005-01-24
a friend told me to try this:

gtf 1152 864 100

and put the result in section monitor like this:

 Section "Monitor"
  Identifier "Generic Monitor"
  HorizSync 30-97
  VertRefresh 50-160
  Option "DPMS"
# 1152x864 @ 100.00 Hz (GTF) hsync: 91.50 kHz; pclk: 143.47 MHz
Modeline "1152x864_100.00"  143.47  1152 1232 1360 1568  864 865 868 915  -HSy nc +Vsync
EndSection

but it gave me again an error, when  I restarted it.

---

