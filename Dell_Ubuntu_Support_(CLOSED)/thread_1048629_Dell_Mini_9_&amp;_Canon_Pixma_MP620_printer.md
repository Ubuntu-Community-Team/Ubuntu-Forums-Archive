---
title: "Dell Mini 9 &amp; Canon Pixma MP620 printer"
date: 2009-01-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vickoxy on 2009-01-23
Hi,
i am really newbie to ubuntu so i need help. I have dell mini 9 and have this lpia issue with the drivers for my canon mp620 (need basic printing).
So, i need to install these two files (drivers):
   1. cnijfilter-common-2.80-1.i386.deb
   2. cnijfilter-mp610series-2.80-2.i386.deb

I described my problem here (as V.):
[http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html](http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html)

But trying to install these files i become this (i will upload two pics):

So, any help will be appreciated. I had Linux Linpus and Acer Aspire Pne and the Printer was working perfectly, and now i want to work it on Ubuntu:D

Thanks

---

### Post by ugm6hr on 2009-01-23
Moved to separate thread.

Have you tried using the System -> Administration -> Printing setup page?

It includes direct downloads of most Linux supported printers, and appears to include the Canon PIXMA MP610.

---

### Post by vickoxy on 2009-01-24
Hi ugm6hr, and thanks for making new thread for me. Yes i did it, but, i have Gutenprint-foomatic 5.0.2. on my Dell. So, it does printing, but the letters are stretched and layout is very strange (all letters have stripes...), as something is not ok. So, i installed the new version (using terminal) 5.2.3. but, although the new drivers are listed in print setup, they are totally unactive (3 new drivers do not work, and two old work but with those errors...)
For normal Ubuntu users gutenprint 5.0.2. should do the work for MP620 (with drivers of MP610), but for dell mini obviously it doesn´t.
So i thought, maybe i can setup only these original two drivers (they worked on Linux Linpus-Fedora and Acer Aspire One) from Canon.
I hope i explained the problem.

P.S. I tried a commercial demo version of **turboprint** (turboprint.de), and everything works just fine with their drivers...

---

### Post by vickoxy on 2009-01-24
So, as said, after installing gutenprint 5.2.3 i have 5 or 6 available drivers that should work-but nothing-there are working only two from 5.0.2 version, with described problems. 
Here are pics of printer  setup:

---

### Post by vickoxy on 2009-01-24
And here is the outprint of driver 5.0.2-and on the bottom of the page is from commercial turboprint (which works just ok). Image quality is bad but i think you can see where the problem is.

---

### Post by vickoxy on 2009-01-25
Hi, i found here some instructions but i think it won´t work with may dell mini? 
[https://answers.launchpad.net/dell-mini/+question/55910](https://answers.launchpad.net/dell-mini/+question/55910)

But it interests me this command *--force-architecture*. Can someone explain me if i can use it to install those .deb drivers and does it have any influence on system?

---

### Post by ugm6hr on 2009-01-25
> **vickoxy said:**
> But it interests me this command *--force-architecture*. Can someone explain me if i can use it to install those .deb drivers and does it have any influence on system?

force-architecture will install those .debs by disregarding the i386 architecture requirement.

You have a lpia rather than i386 kernel, which is very similar.

You could either try running the .deb through the deb2lpia software (as per the other thread you posted in), or use the force-architecture mode.

I'd try the deb2lpia method first.  However, while this will install the .deb, it does not guarantee it will work.

---

### Post by vickoxy on 2009-01-25
Yeeeeeeeeeeeeeeeeeeeeeeeeeeeeesssssssssssssssssss!!!!!!!!



Thank you ugm6hr!!!!:popcorn: I used command force architecture, because it seemed easier to me-but i needed explanation what does it do.

So, now the print quality is excellent-i need only basic printing, so i hope it will help other users.


So, if anyone has Canon mp620, just follows instructions here:
[http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html](http://mp610.blogspot.com/2007/11/setup-canon-pixma-mp600-or-mp610.html)

but to install these two canon drivers use command --force-architecture -i.
Thanks again!

---

