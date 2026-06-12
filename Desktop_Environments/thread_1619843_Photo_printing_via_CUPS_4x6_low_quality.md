---
title: "Photo printing via CUPS 4x6 low quality"
date: 2010-11-12
forum: Desktop Environments
---

### Post by finite9 on 2010-11-12
I've got a dreaded Canon PIXMA MP450, and for the last several years I've been using Turboprint which worked very well, as there really was no free alternative.

I just upgraded to Maverick and I realised I had to buy a new version of Turboprint due to changed dependencies, and after already having bought 2 version of the program, I felt like it was turning into a subscription service... So I tried to get the printer working with CUPS.  Please don't suggest Turboprint as a solution! :)

As it happens, there IS a PIXMA driver in CUPS now!  But only for MP300 (not sure if that's correct) or MP500.  There is no specific MP450 driver.  MP500 driver did not print at all, so I tried MPx00 driver (lower version than I have).

I can print documents just fine, web pages etc all no problem.  But I just tried to print a 4x6 borderless photo and i'm having problems.  Would appreciate it if anyone can help...

Forget the borderless thing for the minute.  I know the reason, and a possible solution is to crop to right size using KDE app (no gnome apps do cropping easily).

When I print the 4x6, the resolution is correct, i.e. it's not pixelated in any way, but it's not printing as a photo... it's printing more like a medium quality newspaper graphic... I can see the dots in the image, especiall in background swaths of colour.  It's not terrible... It does look like a photgraph, but you can see the dots quite clearly.

I have chosen the type of print as "photograph" in CUPS and the resolution is 600x600.

Does anyone know what the problem could be?

Question #2
###########

I can only print via CUPS from Image Viewer.  For some reason, both Gimp and Shotwell show ablank page in the print preview (and print nothing as well), but if I do it through Image Viewer, then print preview works as expected and it actually prints.

I really don't want to have to go back to non-free, Turboprint.

---

### Post by Steeperton on 2010-11-12
Your GIMP problem may be related / fixed by this:
[https://bugs.edge.launchpad.net/ubuntu/+source/gimp/+bug/636329](https://bugs.edge.launchpad.net/ubuntu/+source/gimp/+bug/636329)

---

