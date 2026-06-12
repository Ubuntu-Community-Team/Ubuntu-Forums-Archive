---
title: "DELL N5110 ubuntu &amp; nvidia doesnt work"
date: 2011-07-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wizandrew on 2011-07-15
Dell inspirion N5110 i7 Nvidia GT 525M

i am using Kubuntu 11.04 however i cant make Nvidia drivers to work on this leptop it says they are active but no currently in use and if its added to the xorg.cfg then i gett an error int he end ubuntu only works in low graphics!

all i found about this error is: [http://ubuntuforums.org/showthread.php?t=1786491&highlight=n5110](http://ubuntuforums.org/showthread.php?t=1786491&highlight=n5110)

is there anyway to make it work? (at least so i can use hdmi and normal resolution (and not low graphic settings)?

---

### Post by mikewhatever on 2011-07-18
I suppose you can remove all the Nvidia drivers you installed and use the integrated Intel graphics.

---

### Post by wizandrew on 2011-07-19
yes however HDMI doesn't work only VGA

---

### Post by mikewhatever on 2011-07-19
Perhaps you could try disabling the Intel graphics in the BIOS and use the Nvidia card only. Have you tried that?

---

### Post by wizandrew on 2011-07-20
i wish it was that easy however i didn't find any such option in the bios :\

---

### Post by seif12 on 2011-09-11
I have a problem like this i have a Dell n5110 with Nvidia graphic card , and i installed Ubuntu 10.04 . but the Nvidia Card is not detected on Additional driver so i installed the Drivers from the website and than X server won't to start i got an error message "no screen found" . The sound don't work neither .

---

### Post by faberglas on 2011-09-25
Unfortunately, I recommended that a friend buy an Inspiron because Ubuntu ran on my 1545. I've wasted several hours trying to get the screen on this n5110 to display properly. Nvidia says to go to Hell, er, Dell for a solution. We all know how they treat customers.  ](*,)

---

### Post by m_pahlevanzadeh on 2011-10-07
I installed nvidia driver from the following guide on Debian , i think you can follow the given guide and install nvidia driver, i have inspiron n5110 and i has another problem. if possible, you can put your email address in via PM that we'll have share our experiences.
Debian guide:
[http://wiki.debian.org/NvidiaGraphicsDrivers]("http://wiki.debian.org/NvidiaGraphicsDrivers")

---

### Post by shevek. on 2012-01-11
I have a N5110 (Ubuntu 11.10) and opted by disabling nvidia and enabling 3D acceleration in the Intel card (it has both cards, check Nvidia Optimus). It also boosts battery life. In detail:
[http://ubuntuforums.org/showpost.php?p=11603104&postcount=28](http://ubuntuforums.org/showpost.php?p=11603104&postcount=28)

---

### Post by wizandrew on 2012-01-11
> **shevek. said:**
> I have a N5110 (Ubuntu 11.10) and opted by disabling nvidia and enabling 3D acceleration in the Intel card (it has both cards, check Nvidia Optimus). It also boosts battery life. In detail:
[http://ubuntuforums.org/showpost.php?p=11603104&postcount=28](http://ubuntuforums.org/showpost.php?p=11603104&postcount=28)

so does HDMI work for you or its just VGA?

---

### Post by shevek. on 2012-01-16
HDMI audio doesn't work, HDMI video I didn't try it (with the HDMI cable) as I don't have such need.

HTH

---

### Post by wizandrew on 2012-01-18
well from what i tried it doesn't work. :(
so i would love to know a way to enable it .:confused:

---

