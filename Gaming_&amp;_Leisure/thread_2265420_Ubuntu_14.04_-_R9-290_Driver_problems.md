---
title: "Ubuntu 14.04 - R9-290 Driver problems"
date: 2015-02-15
forum: Gaming &amp; Leisure
---

### Post by adam124 on 2015-02-15
Alright,  for the last couple days I have been racking my brain trying to figure  out how to get this damn GPU to fully function on Ubuntu 14.04 and Linux  Mint 17.1, to no success.

  I have installed the required drivers from the Software Manager, tried beta drivers from AMD and the stable drivers **(fglrx-amdcccle-updates)**. This card is detected and the drivers get installed successfully however:

  
[LIST]
[*]The GPU idle temp is around 50 degrees 
[*]The GPU core clock **never **increases over 3-500MHz (making games lag) *[Should be around 1100Mhz while gaming]* 
[*]The GPU voltage is unable to be retrieved 
[*]The GPU fan information is unable to be retrieved 
[*]AMD Overdrive is unable to work 
[/LIST]
  
All the above problems obviously point to a driver problem, however I have no idea what I'm doing wrong. 
  [B]I have also installed the  *RadeonSI* Gallium3D drivers, this did not change anything, performance was slightly better with the fglrx driver.
[/B]
I am starting to think that driver support for higher end cards is just really bad?

_Relative Specs:_
**GPU**: AMD Radeon R9-290
**CPU**: i5-4590
**OS**: Ubuntu 14.04 (64bit)

---

### Post by mörgæs on 2015-02-15
[http://leftcoastgeek.blogspot.com/](http://leftcoastgeek.blogspot.com/)

---

### Post by R33D3M33R on 2015-02-15
Try updating drivers by adding this PPA: [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

Don't forget to install ppa-purge before update: sudo apt-get install ppa-purge
This way you can remove the PPA if anything is wrong: sudo ppa-purge ppa:oibaf/graphics-drivers

Also, some changes are coming to the kernels: [http://www.phoronix.com/scan.php?page=news_item&px=AMD-Hawaii-Linux-3.20-Reclockin](http://www.phoronix.com/scan.php?page=news_item&px=AMD-Hawaii-Linux-3.20-Reclockin)

---

