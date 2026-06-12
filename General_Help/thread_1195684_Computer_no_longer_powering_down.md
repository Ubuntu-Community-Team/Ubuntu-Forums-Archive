---
title: "Computer no longer powering down"
date: 2009-06-24
forum: General Help
---

### Post by ACupOfCoffee on 2009-06-24
This started about a week ago. Was working fine beforehand. This is my mom's desktop and the only room in the house with a suitable place for it was the kitchen. I have odd work hours so I often wind up eating dinner around the time everyone else in my household is winding down for the day and getting ready for bed. Sometime last week I'd notice a single line of text on the monitor after my mom had shut the computer down and walked away thinking it was off. Text is some numbers and then Powerdown. I have to use the power button to actually get it off. Otherwise everything works fine.
 
Specs: Elitegroup mobo
Core 2 Duo
Intel integrated graphics
USB wireless NIC
1 GB RAM
 
Any help would be appreciated because if I don't get this fixed it's going to run up our electric bill even more then 105 degree weather and no rain in over a month already has.

---

### Post by Soul-Sing on 2009-06-24
try this: ```
sudo shutdown -h now
```

---

### Post by VCoolio on 2009-06-24
[This little fix]("http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_%28Intrepid_Ibex%29_on_a_Thinkpad_T400#Shutdown_freezes_sometimes") helped me a while ago (with Intrepid), give it a shot. Other than that I can only give a workaround: use ```
sudo shutdown -hP now
```. Or if you make a launcher for that on your panel make that gksudo. Good luck.

---

### Post by ACupOfCoffee on 2009-06-29
Neither one of those causes anything different. It gets all the way to the point where it should turn off but instead of doing that it displays two sets of numbers (different every time) inside brackets and separated by a period. Following that on the same line are the words "Power down". The power LED also turns off. I think this started right around the time I updated the kernel through Synaptic.

The only way I can actually get it off is to either hold the power button or unplug it.

---

### Post by ACupOfCoffee on 2009-07-03
Fixed it by updating the BIOS.

---

