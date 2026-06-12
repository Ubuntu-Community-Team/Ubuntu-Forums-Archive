---
title: "I need to speed up a program"
date: 2009-01-06
forum: General Help
---

### Post by SillyKirby on 2009-01-06
I have an application that uses 1.03G of RAM. System monitor says it also uses 1.03G of Cache and 0.13G of Buffer in RAM when the program is running. 

My mobo is ASUS M3N78 Pro AMD2+; my CPU is AMD Phenom X4 9650 Quad Core; my memory is Corsair Twin 2x 4096-6400C5 DHX; PC2-6400 4GB kit; 5,5,5,18 latency DDR800 in Dual Channel configuration, my operating system is UBUNTU 8.10 Intrepid Ibex, 64bit. 

I think it would run faster if I upgraded to 4GB of1066 memory, but Asus support says:

“The limitation for 1066 memory is a total of 2 1 gig chips. But at 800 Mhz it can run up to 8 gigs(in the hardware, but the operating systems are limited to 3-3.5 gigs ) You do not want to mix the memory types. recommendation is to go to the 4 gig on the 800mhz to keep the dual channel nature, call the ram manufacturer and get the settings for the ram and then call us and we can help you set the timings in the system to ensure stability.”
Regards,

Nicholas Pogue
Asus Support Team

I am worried that just 2 Gig of RAM will not hold the full memory requirements of the app. Does anyone know what will happen if I install 4 Gig of 1066 RAM in a Dual Channel mode? Anybody have any other ideas about how I can speed up the program with hardware?

---

### Post by sdennie on 2009-01-06
I'm not sure if you can include the cache numbers in your application memory requirements.  I don't know of any way to directly correlate how much cache an application is "using".  The only way adding more memory is likely to speedup the app is if you are seeing very large amounts of disk activity during the entire runtime of the application or on successive runs of an application.  If that's not the case, adding more memory probably won't change how fast that particular application will run.

---

### Post by SillyKirby on 2009-01-06
Vor, thanks for the response. What i was thinking is that by moving from 800Mhz memory sticks to 1066Mhz the program would access the data in RAM quicker, which would make the app run quicker. Not so? I sort of deduce from your reply that i don't have to worry about cache, hence my apps memory would fit on the 2gig of 1066Mhz ASUS says will work. worth a try. 

Any other thoughts? Silly

---

### Post by sdennie on 2009-01-06
Sorry, I don't think I completely read your post.  :)

It's hard to say if going to 1066 sticks will speed up the application.  Depending on the application, it could make a noticeable difference but, it's very unlikely that difference will be anywhere near the 1.33x difference in RAM speed.  The only way to really know is to understand your app very, very well or to simply try it.

---

### Post by SillyKirby on 2009-01-07
Vor, ok, best advice i have had:) i will buy the 1066 memory and give it a try. i think it really will help, cuz the app is just running through a big bunch of flops, and memory speed will really count .... i think? Silly

---

