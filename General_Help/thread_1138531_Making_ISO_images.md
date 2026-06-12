---
title: "Making ISO images"
date: 2009-04-26
forum: General Help
---

### Post by B4RR13N705 on 2009-04-26
Hi, i have a few movies at home, and i want to make an ISO to my Ubuntu.
Does anybody know how to do this??

---

### Post by joeyknuccione on 2009-04-26
> **B4RR13N705 said:**
> Hi, i have a few movies at home, and i want to make an ISO to my Ubuntu.
Does anybody know how to do this??
In a terminal do:

cat /dev/scd0 > /home/yourfolder/nameforimage.iso

Where /dev/scd0 is your cd/dvd drive
Where /home/yourfolder is the name of your personal folder
Where /home/yourfolder/nameforimage.iso is the name you wish for the ISO

Or you can use Brasero:

Applications > Sound and Video > Brasero Disc Burner
Then look at left on the bottom for "Burn image"

---

### Post by B4RR13N705 on 2009-04-26
Im having some troubles. I want to copy an original movie DVD, i tried everything, but the only thing that i get is "Input/Ouput Error".
In windows i used to do this with DVD shrink, is there a free alternative?

---

### Post by B4RR13N705 on 2009-04-26
Please note that i dont want to do something illegal, i just bought the movie, and i want to uploaded it to my mythbuntu PC to watch in my home-theatre :) :popcorn:

---

### Post by Old_Grey_Wolf on 2009-04-26
Install K9Copy from the repos, and see if that works for you.

---

### Post by oldos2er on 2009-04-26
You should be able to right-click on the DVD icon, choose Copy Disc, and copy it to a file image.

---

### Post by B4RR13N705 on 2009-04-26
It works fine, it starts extracting, but then it crash! I cant get anything. Is there another option?

---

### Post by coffeecat on 2009-04-26
> **B4RR13N705 said:**
> It works fine, it starts extracting, but then it crash! I cant get anything. Is there another option?

You need libdvdcss2. Install it from [medibuntu](http://www.medibuntu.org/). You don't need to add the medibuntu repository to your system if you don't want to. Instead, just download the libdvdcss2*.deb package appropriate to your system. Put it on your desktop, double-click it and it will install itself.

If you install libdvdcss2, k9copy won't crash.

---

### Post by B4RR13N705 on 2009-04-26
Thanx! Problem solved!

---

