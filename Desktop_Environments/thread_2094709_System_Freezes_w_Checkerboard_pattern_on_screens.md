---
title: "System Freezes w/ Checkerboard pattern on screens"
date: 2012-12-14
forum: Desktop Environments
---

### Post by ComtreadBob on 2012-12-14
Greetings All,

Long time reader, and as you can see first time poster - I was not able to find a solution
to an "issue" I am having :-)

I recently added a Radeon HD 5450 to our Ubunto 10.04 LTS system (Dell Optiplex 745)
with all the latest updates.

The video card upgrade (from the on board video) was so the workstation can have 2
screens.

All seemed to be working fine, until randomly the system locks up and we have 
"checkerboard" pattern on the screens - the system does not respond to keyboard
commands to go to a terminal screen.  By Randomly - the system was fine one day for 8 hours, the next day it does this after 5-15 mins of logging (on these systems only firefox and open office are used)

Any help in this matter would be greatly appreciated! :-D

The "screenshots" taken with my phone can be seen below:


[IMG]http://t.comtread.net/IMG_20121108_092132.jpg[/IMG]


[IMG]http://t.comtread.net/IMG_20121108_092137.jpg[/IMG]

Thanks,

Bob

---

### Post by QIII on 2012-12-14
If you would, please post images as thumbnails so that those with low bandwidth are not disadvantaged.

You said you added a card.  Are you running both monitors off the same card?  What is the other GPU OEM and model?  How did you install the driver?  Did you disable the onboard video in BIOS or does it automatically do so when a dedicated card is added?

---

### Post by ComtreadBob on 2012-12-17
Hello QIII,

Thanks for the tip - just resized the "screenshots"

Yes - both monitors are connected to the same video card

The integrated video card is disabled automatically when a graphics card is installed - verified, by trying to boot with a monitor connected to the onboard video card - and the system told me to move it to the add on video card.

Any ideas?

Thanks!

---

### Post by RitzBitzN on 2012-12-19
Open terminal, and then type in 'sudo apt-get install lm-sensors', if you have not already installed it, and then type in just 'sensors', and you should see an output like:

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +51.0°C  (high = +95.0°C, crit = +105.0°C)
Core 2:       +47.0°C  (high = +95.0°C, crit = +105.0°C)

Check if the Temperature for Core 0/2/n is greater than its high or critical. If it is critical, I assume the card would shut down, but if it is just high, maybe try cleaning the box or seeing if anything is preventing the fan from spinning.

---

