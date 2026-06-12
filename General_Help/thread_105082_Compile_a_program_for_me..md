---
title: "Compile a program for me."
date: 2005-12-17
forum: General Help
---

### Post by Vilhelmo on 2005-12-17
I need to use a program called Gemu to edit audio routes for my emu10k1 based soundcard. I've been trying to compile and I've been installing a lot of packages to be able to compile it.. But it wont compile properly. 

So I would be forever grateful if someone could compile the program for me on a i386 based computer with ubuntu 2.6.12-10. 
The link: [http://www.roadfeldt.com/gemu/features.html]("http://www.roadfeldt.com/gemu/features.html")

This is the last thing that is keeping me from removing windows and beginning to  use ubuntu.

---

### Post by endersshadow on 2005-12-17
Run these commands in the terminal:

```
sudo apt-get install alien
cd
wget 'http://optusnet.dl.sourceforge.net/sourceforge/gemu/gemu-0.8-1.i386.rpm'
sudo alien gemu-0.8-1.i386.rpm
sudo dpkg -i gemu_0.8-2.i386.deb
sudo -k
```

If the line, "sudo dpkg -i gemu_0.8-2.i386.deb" returns an error, use the ls command to find out what the .deb file is called, and use that name instead of the one given.

---

### Post by soulestream on 2005-12-17
you might want to learn to compile software. 

If you would like to try to figure it out, posting why it won't compile or the error it gives would be useful.


soule

---

### Post by Vilhelmo on 2005-12-17
Thanks for the help, I was able to open the program but with a "segmentation error", so i found out what was wrong when I tried to compile the first time, I was missing a program called automake.. Anyway, I think i could compile now, but not without trouble. 
I am busy until tuesday, so I will have to try to finish the work then.. 

I'll come back later with a report how it turned out.. 
btw Thanks for the quick answer...

---

### Post by Vilhelmo on 2005-12-18
Ok I was able to run the program but when it opens, it turns up a "segmentation error". I was also able to compile it (with a lot of warnings) and when I test it there it also just says error when I open it. So my soloution to this problem will be to get myself a new soundcard ( an old one i can get for free :P).

Please don't blame ubuntu for this problem, cause in windows the soundcard has done nothing but caused me trouble (but still it comes sound out of it), so I really don't expected linux to support the soundcard. But since I am such a music addict it's important with great sound from my computer ;) Thanks for the help anyway!

---

### Post by Vilhelmo on 2005-12-20
Hi again! 
I finally solved my sound issue. The solution: get a new soundcard. 
My experience of ubuntu:

Good:
-The new soundcard worked perfectly after I had put it in. :) (using the alsa-module)
-Ubuntu is user friendly, as long as you don't got unusual and advanced hardware.
Bad:
-Advanced hardware (as my last soundcard) is very hard, maybe impossible to support. If there would be such a program as ndiswrapper, that helped me with my wireless network card, but adopted to use windows drivers to support hardware in general in linux, I am sure it would help a lot of people with hardware problems. 

I understand that the heart of linux is that it don't use the same system as windows, but this is just an idea, maybe impossible to realise. 

Thanks to this forum that helped me get some basic ubuntu knowledge.

---

