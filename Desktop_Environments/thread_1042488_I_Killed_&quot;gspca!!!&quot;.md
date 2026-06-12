---
title: "I Killed &quot;gspca!!!&quot;"
date: 2009-01-17
forum: Desktop Environments
---

### Post by keithld on 2009-01-17
I finally got my Logitech Webcam working and I was playing around with the gamma in the options file and saved it... Then I did a sudo rrmod gspca in a terminal Or at least that is what I typed and I now get this error:

ERROR: Module gspca does not exist in /proc/modules

If I do sudo modprobe gspca I get the following:

FATAL: Error inserting gspca (/lib/modules/2.6.27-0-generic/kernel/drivers/video/gspca.ko) : Invalid argument

So I guess I somehow deleted it...  Any way to get that corrected ????


Thanks guys...


Keith

---

### Post by keithld on 2009-01-17
Well while being bored I installed and compiled gspca-source then I deleted the gspca.ko file from the library sub-folders then deleted the gspcav1-20071224 tar files and the folder then I re downloaded everything and started over with adding the patch and compiling the driver and following all the directions in Actionshrimps tutorial...

So my Logitech Quickcam E2500 Connect is working once again...

Oh yeah, it seems the option to flag a post as "SOLVED" is no longer available or I can't seem to find it...  :D

---

