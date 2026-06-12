---
title: "Ubuntu with canon ip4000 printing half size"
date: 2006-06-09
forum: Desktop Environments
---

### Post by bohboh on 2006-06-09
Hi All

Having battled with it for half a day i have managed to get my printer to print a complete page.

The issue now is that it will only print it at half the size, so it prints the entire page but resizes it down (whilst maintaining the aspect ratio) to approx one third of the original a4.

I have checked the printer properties and it is set to A4.

Any ideas?

---

### Post by Dr. Nick on 2006-06-09
[quote=bohboh]Hi All

Having battled with it for half a day i have managed to get my printer to print a complete page.

The issue now is that it will only print it at half the size, so it prints the entire page but resizes it down (whilst maintaining the aspect ratio) to approx one third of the original a4.

I have checked the printer properties and it is set to A4.

Any ideas?[/quote]

I have the ip3000 and can say it is very sensitive to drivers. Which are you using?

If you havent already try the bjc-7000-bjc800 drivers. Thier are like 3 drivers that have 7000 and 800 in the name i think. I had best luck with the one that had the "g" word on it. I did my testing by trial and error lol. Hope that helps

---

### Post by lucia_engel on 2006-06-09
I have the same printer and had a similar problem before (it resizes itself to a quarter of the page)...but then I switched to "Letter" size and it worked, I'm not sure why.

---

### Post by bohboh on 2006-06-11
Managed to get it working with turboprint (latest) and cups 1.2.1 which i had to download and install manually. For some reason apt-get would only download 1.2.0.

Got it from here [Cups 1.2.1]("http://linux.softpedia.com/get/Printing/Common-UNIX-Printing-System-10427.shtml")

---

### Post by davidsrsb on 2006-06-15
The ip4000 driver is a major regression, I had my ip4000 running well on hoary using the s360 (or was it s630?) driver with just a small colour hue error.
Now the yellow head is misaligned by a couple of inches vertically

Not sure why Dapper is using the very broken first release of cups 1.2

---

### Post by davidsrsb on 2006-06-16
Update
the s630 driver still works, but uses the sheet feeder only.

For some strange reason the ip4000 driver has yellow and black treat the paper size as 50% of true and the other two cartridges 50% vertical and 75% horizontal.

---

### Post by davidsrsb on 2006-07-09
This morning synaptics an upgrade to cups 1.2.1 in the repositories. I installed it but no change, except (mis)printing is now much slower.
This evening another machine cannot find the update, odd?

---

### Post by paul_h on 2006-07-15
Thanks Dr Nick !!

Your idea of installing the ip4000 with the bjc7000 driver works well !!

I tested printing win B&W and color, on A4 in the top sheet feeder, 6x4 color photo from the cassette, and even CD printing. All worked well, although I will need to do a little to deepen the color in the photo printing.

This has been a huge break-through for me as I have had great expectations of Ubuntu. However, an operating system that could not print properly on any of my printers .. is useless. After months of fiddling with Ubuntu I can now get into it seriously and free myself (well, almost) from MS.

Thanks again.

---

### Post by Dr. Nick on 2006-07-15
Glad it worked for you, I started using it with an older canon printer, when it died and we got the ip3000 I thought I would try the same one and sure enough it worked, I recommend the bjc7000 driver to anyone with a later model canon printer that doesnt have drivers, It seems to be very versitle.

---

### Post by davidsrsb on 2006-08-23
The secret is to use the cups webpage to set up your printer options
To do this make sure that user cupsys is a member of group shadow

---

### Post by Dr. Nick on 2006-08-24
> **davidsrsb said:**
> The secret is to use the cups webpage to set up your printer options
To do this make sure that user cupsys is a member of group shadow


Will adding the user knock out the administraative lock in the cups page?

For anyone interested to get to that page go to 

[http://localhost:631](http://localhost:631)

I just checked and didnt see any errors about cups admin like thier used to be, Guess they changed it

---

### Post by koshari on 2006-08-24
> **paul_h said:**
> Thanks Dr Nick !!

Your idea of installing the ip4000 with the bjc7000 driver works well !!

I tested printing win B&W and color, on A4 in the top sheet feeder, 6x4 color photo from the cassette, and even CD printing. All worked well, 

Thanks again.

i have an IP3000 and were wondering how you went about printing cds, did you use a template? is there a cd tray option on the bjc7000 drivers?

at the moment i have turboprint drivers set up for cd printing but it isnt real user friendly, and the print tools dont work, 

canon linux support has proven to be a pretty patchy affair for the ip*000 series of printers if you want to do anything more than very basic printing :-(

---

### Post by Dr. Nick on 2006-08-24
eh, last I knew the linux drivers for any canon did not support cd tray or duplex printing. I can live without the duplex as that is easy to do manually, but as far as I know cd printing isnt much of a option. 

If you try you may get it, I have a us ver of the printer which is sorta crippled, so I had to make my own tray and do a few other things to even get it to work in windows, I wasnt impressed so I never tried it in linux

---

### Post by Johan! on 2006-08-24
[Here]("http://www.ubuntuforums.org/showthread.php?p=1341911#post1341911")'s how I installed my IP4000.

---

