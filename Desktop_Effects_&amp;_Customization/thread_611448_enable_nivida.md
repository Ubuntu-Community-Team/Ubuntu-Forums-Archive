---
title: "enable nivida"
date: 2007-11-12
forum: Desktop Effects &amp; Customization
---

### Post by onlyproductions on 2007-11-12
hi, i got ubuntu to wrk on my friends comp, i click on desktop effects and it says u need to enable nivida driver then it has two buttons cancel and enable driver.i click the latter and it says please run desktop effects after restarting the computer with the new graphics driver active. so i restart, click on the desktop effects and the same thing happens, how do i "activate the driver"

---

### Post by solar george on 2007-11-13
Try System > Administration > Restricted Drivers Manger

---

### Post by onlyproductions on 2007-11-13
> **onlyproductions said:**
> hi, i got ubuntu to wrk on my friends comp, i click on desktop effects and it says u need to enable nivida driver then it has two buttons cancel and enable driver.i click the latter and it says please run desktop effects after restarting the computer with the new graphics driver active. so i restart, click on the desktop effects and the same thing happens, how do i "activate the driver"

i did, but when i check the radio box it blinks and goes back to not being checked.

---

### Post by AndyCR on 2007-11-13
This is a bug I reported months ago during the days of Feisty, and they told me it would be fixed... Not sure why it persists. Click System->Administration->Synaptic and click Reload. It should be installable after that. This is caused by not having an internet connection at install-time, thus the software sources aren't refreshed at install time; the restricted driver manager assumes it updated during install.

---

### Post by onlyproductions on 2007-11-14
> **AndyCR said:**
> This is a bug I reported months ago during the days of Feisty, and they told me it would be fixed... Not sure why it persists. Click System->Administration->Synaptic and click Reload. It should be installable after that. This is caused by not having an internet connection at install-time, thus the software sources aren't refreshed at install time; the restricted driver manager assumes it updated during install.

thanx man it wrks perfectly now

---

