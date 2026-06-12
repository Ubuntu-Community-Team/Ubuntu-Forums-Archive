---
title: "MP Bios issue and more"
date: 2009-06-23
forum: General Help
---

### Post by Nubi505 on 2009-06-23
In both 9.04 and 8.04 I get an MP Bios bug at the black boot up screen before the Ubuntu logo/loading screen. 

"MP-BIOS bug 8254 timer not connected" <-- It goes kinda fast, so I hope those are the right numbers. 

I can't really tell if the bug is something that needs solving, but I'm also getting very frequent mouse freezes in both versions and infrequent keyboard freezes. I have no idea if they are connected though.

Anyway, is there a way to solve the MP-BIOS bug? If it involves the Terminal, please be specific. I'm new to the concept. 

Thanks.

---

### Post by LADmaticCA on 2009-07-13
I've have this problem too and cannot find a solution anywhere. My systems works just fine and all but this error holds up my boot process for a good 10 seconds.

---

### Post by GnuUserHere on 2009-08-16
I have the same error on an Acer Aspire 5515 Running Ubuntu ver. 9.4 then to make matters worse the battery does not charge when it did charge prior to the install of Ubuntu.

1.) If I run in terminal :  acpi
   
I get this message: Battery 0: Full, 0%    

2.) If I run in terminal : acpi-V

I get this message : bash: acpi-V: command not found

I installed yacpi
Ran it and receive the following:

* YACPI 3.0 by Nico Golde                                                       

BAT1 Capacity [                         ]  0%

BAT1 status: charged   

AC adapter status: on 

Temperature: 48 degrees C

CPU governor: ondemand

CPU frequency: 800/1600 MHz

BUT...the battery will not keep the laptop alive..nor will it boot w/o being plugged in to AC source.


I checked other posts re: batteries and ACPI  and saw that it might be a BIOS update required to fix these woes...alas...I have the only BIOS available  to the best of my knowledge a Phoenix BIOS 1.1 .
Just for kicks and giggles I went to the Acer site to seek a BIOS update there was one!
I downloaded it...unzipped it..tried to run it...oh...bugger! ....It was the wrong one..and Only one claiming to be "The" BIOS update for the Acer Aspire 5515...and would not burn.

Anyone got a clue as to what can be done to cure this problem?
:confused:


I got another battery...brand new..It will not charge either :(

---

