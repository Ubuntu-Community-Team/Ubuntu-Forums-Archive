---
title: "Photo Printing - Help!"
date: 2008-11-14
forum: Desktop Environments
---

### Post by smirnoff76 on 2008-11-14
I am using 8.10 and have just got a new printer however am having problems printing to photo paper sized 6 X 4". 

i am trying various app's and the prints either come out with botched margins, centred for an a4 sheet etc. 

Can anyone please offer any advice for photo printing especially for paper sized 6" X 4". 

any help would be seriously appreciated!!

---

### Post by Idaho Dan on 2008-11-14
That is a good question, I have not tried that since I switched to Ubuntu, and I know I will want to.
I hope some one knows more about this than I do and can help you.
I'll try when I get home in a couple of hours.
If I have good luck I will post it.

---

### Post by binbash on 2008-11-14
Did you try : 

gnome-photo-printer , photoprint

---

### Post by smirnoff76 on 2008-11-15
So far I have tried Gnome Photo Printer, Google Picassa which wont print at all?? and also FLphoto no luck with any of them

---

### Post by sofoxy on 2009-05-27
I tried jaunty but photo printing is also not good. Still needs alot of work on the resolution. I tried it on openoffice drawing. I'm using canon pixma mp145.

---

### Post by blecha on 2009-09-16
If I understand correctly, you have the same problem as I do; i.e the apps. will not print on the photo Tray. 

I only recently switched from 6.06 Dapper Drake to 8.04 Hardy Heron (I am mainly using my computer for ... computing) just because I was unable to access my bank account. When doing that the printserver in my router (U.S. Robotics Wireless MAXg ADSL Gateway) stopped working - problem solved by downloading the last beta-version of U.S. Robotics firmware - and the Gimp printing interface which I used for photo printing appeared to be changed in 2.4.5 distributed with 8.04 with consenquence that photo Tray is no more reckognised. I am using HP PhotoSmart 7350 Foomatic/hpijs, hpijs 2.8.2 driver and I created under CUPS 1.3.7 printer "photo" which is configured to print to the photo tray and to use the high quality printing mode. The test page is printing OK to the photo Tray. I tried GIMP, F-spot and gThumb but all of them are trying to use the default tray and the printer is asking to remove the photo Tray. 

Therefore I am using direct printing through command line "lpr -Pphoto my_photo.jpg" where my_photo.jpg is just the original photo with changed resolution so as to have the size within the photo paper limit (for my image 2736x3648 px the resolution 800px/inch is OK). You can do it either in GIMP or directly with command " convert -density 800x800 -crop 0x0 my_original.jpg my_photo.jpg".

I feel like an old *** not to be able to use properly such a nicely looking apps., is there realy no way in recent releases to print photographs from apps. to the photo Tray ?

---

### Post by StuartN on 2009-09-16
I have found that since printers included a memory card slot and computerless printing, it has solved almost all my printing problems. I put my photos onto a USB drive and print them from that. I have actually never connected my current photoprinter to my PC. I get more hassle with draft printing on an old inkjet connected to the PC.

---

### Post by blegs38552 on 2009-09-22
That is one answer, I guess. Edit file files in GIMP (for example), save them to an SD card and print the files on the SD card directly. Not ideal for sure, but it works.

I use Adobe Photoshop Elements in Windows 7 RTM and print directly to my Epson Picturemate printer through the USB port with no problem. This gives me greater control over the print process and is certainly the way to go in Windows.

I guess, in some ways, Windows still has Linux beat.

---

