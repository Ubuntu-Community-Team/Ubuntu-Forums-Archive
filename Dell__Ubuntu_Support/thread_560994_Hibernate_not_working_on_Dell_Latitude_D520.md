---
title: "Hibernate not working on Dell Latitude D520"
date: 2007-09-27
forum: Dell  Ubuntu Support
---

### Post by ashleywiz on 2007-09-27
my name is Ashley Delaney, i reside in goa, India. i have a dell latitude d520 notebook with pentium dual core 2300, 1 gb ram and 80 gb running ubuntu edge 6.10

i am facing problems with my installation where EVERYTHING works EXCEPT he hibernate feature,

when i click on hibernate in gnome, the hdd light flashes, the laptop goes off after sometime, but when resuming after i press the power button, it attempts to start the x server and finally gives me a text dialog box with a little ok button to press telling me that the machined failed to bring up the display. this may be a problem with my driver it says. suspend works sometimes on the same machine and at times it gives this same exact error message
is this a driver issue? can anyone  help me?
please note that i have 2gb as a swap more than double the ram available. i have an onboard GMA 950 card, the driver being used in xorg.conf is i810.

thanks
Ashley

---

### Post by ashleywiz on 2007-09-27
Hey!!!! i managed to solve it,

i first installed uswsusp
than tried a hibernate, it worked!!!! but hello why didnt my wireless network come up? i tried everything but only after i removed nad restarted the module did it start to work again, so 
i did gedit /etc/default/acpi-support and  did the following changes
commented out the following as it wasnt running on my machine :-)
#STOP_SERVICES="mysql"
and added the following
MODULES="ipw3945" to enable the module to be relaoded when working again

this enabled the sysem to detect my wireless network adn get me up and running immediatly.
i'm soo happy i can now resume work in 30 seconds flat!!!.

Thanks
Ashley

---

