---
title: "ATI 3d accelerated cards?"
date: 2006-10-07
forum: Desktop Environments
---

### Post by lemonsCC on 2006-10-07
This may be a odd question to ask, but how would you know if you have a "3d accelerated card?"  and how would you know if it is working to its fullest potential?

I am itching to play with Beryl, even tho I KNOW it will end up breaking something...and 3d acceleration is required for this.  My computer is not the newest, but gets the job done nicely.

---

### Post by pay on 2006-10-07
What specific card do you have? What are you planning on using beryl in confunction with? I beleive that the newer ATi cards aren't capable with the fglrx driver running AIGLX yet. Some order cards with the radeon driver will be able though. You can use XGl with the fglrx driver. To find out what driver you are using type in fglrxinfo.

---

### Post by lemonsCC on 2006-10-07
The Card is a Rage 128 Pro Ultra TF

fglrxinfo produces:
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

---

### Post by galego on 2006-10-09
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually")

go to that site, you will find ou thow to get your card 3d ready and if it is capable of running fglrx. right now you do not have 3D capabilities. (the driver is not a 3D driver)

---

### Post by elektronaut on 2006-12-08
That wiki page seems to be about Radeon cards, the OP has a Rage.

---

