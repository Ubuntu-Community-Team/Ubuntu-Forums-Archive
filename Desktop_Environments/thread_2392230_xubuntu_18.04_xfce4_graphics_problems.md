---
title: "xubuntu 18.04 xfce4 graphics problems"
date: 2018-05-18
forum: Desktop Environments
---

### Post by davidlondonuk on 2018-05-18
Hi All,

I recently installed xubuntu 18.04 and am very happy with the new distro - but there is one really annoying problem:

The desktop will work fine for hours then all of a sudden window widgets go black, top panel and desktop icons disappear and I have to struggle to log out and in again to cure the problem. This problem occurs more quickly if I use java apps like BlueJ for java development.

On 16.04 I could use the nvidia driver 304.131 but this is not available. Nvidia now offer 334.21 driver for my card (quadro nvs 285) which is also not available. The nouveau driver is working reasonably well but I am sure it is the cause of the graphics problems. On 16.04 if I installed the nvidia driver I had no graphics problems at all.

I really don't want to manually install the nvidia 334.21 driver, I have never used it and am not sure it will work as well as 304.131.

Any ideas on a cure for this problem?

---

### Post by Autodave on 2018-05-18
All of the drivers you mentioned are in the repositories: you can install from there.  Have you tried going to Settings -> Additional Drivers to see if any are found/recommended there?

---

### Post by davidlondonuk on 2018-05-19
Thanks Autodave,

I did check the repos and the ppa repos, the 304.131 driver is no longer supported by nvidia so ubuntu have pulled it - software & updates shows no drivers for my card. The problem I get is the desktop panel, widgets etc start to degrade in appearance and then disappear - I can't think of any other cause but the video driver.

---

### Post by Autodave on 2018-05-19
I am sorry about that: the 340 driver is still available, but not the 304: my mistake.

Would the 304 driver cure your problem? Possibly. But I really doubt it. The fact that it runs for hours before the problem occurs leads me to believe that something is overheating. Have you cleaned the machine recently? Used compressed air to blow the dirt off of the CPU and GPU?  Cooling fans clean and operational?

If you are still convinced that it is a driver problem, it may be time to upgrade your graphics card. A 4 gig Nvidia card on Amazon can be had for less than $100 and a 2 gig Nvidia for less than $50. Should youi decide to upgrade, look at the card you want and then go to Nvidia's site and check for Linux driver availability.

---

