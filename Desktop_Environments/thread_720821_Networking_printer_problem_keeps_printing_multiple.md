---
title: "Networking printer problem: keeps printing multiple copies!"
date: 2008-03-10
forum: Desktop Environments
---

### Post by sayyeah on 2008-03-10
Hi folks, I'm using ubuntu 7.10 on my laptop.
I have a problem when I print some papers to network printers using IPP.

Everything is fine until it prints the first copy, but after some random time(about 5~10minutes) it keeps printing the same copy again and again without any notice!
On the "Document print status" window, the status always turns to "held" after the printing is finished. I have to manually "cancel" it and refresh to actually erase that message. Then it stops well.

I tried with 3 different network printers with double checking the option to make sure to print only 1 copy(which is obvious), but the result was the same.

Yesterday I printed more than 100 pages for a single document which is just 15 pages long..what a mess.
On windows XP, it works without any problem.

Does anyone have a clue?

I tried removing and reinstalling cups related package too but didn't work.
Also, cupsd is always running even though I don't use my PC as any printer server. I'm not sure it is the right thing.

Thanks in advance.

---

### Post by thewho? on 2008-03-18
IPP uses a postscript driver.  First, make sure you are using a postscript driver, and if you are try another one.  There are bunch of them you can use.

---

### Post by sayyeah on 2008-03-18
Thanks, I'll try that out.

---

### Post by insatible on 2008-05-23
I have the same problem now, and the problem continues even if I cancel all the things in document print status, or delete printer..
now I am using my laptop with windows, because I have to shut down the ubuntu computer to avoid another copy...

---

