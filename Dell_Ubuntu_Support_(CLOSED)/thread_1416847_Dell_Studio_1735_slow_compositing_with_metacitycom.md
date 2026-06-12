---
title: "Dell Studio 1735 slow compositing with metacity/compiz! HELP!"
date: 2010-02-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mounty1512 on 2010-02-26
Hi,I am new to Ubuntu but have dabbed into opensuse a bit on my old computer a few years ago. I have installed Ubuntu 9.10 onto my Dell Studio 1735 Laptop. I had no real problems with anything until i started using Compositing programs (not sure if that is the right term to use but I'm new to this so not exactly sure on what the correct terminology is). Then only real feature i would like to be able to run is the Avant Window Manager. i first tried Compiz and it worked but whenever i tried switching windows or opening lists it would temporarily freeze the system for a few seconds. I've tried to find solutions but have had no luck. I also tried enabling the compositing feature in metacity but had the exact same result. I cant understand why it runs so slowly and don't have any idea of how to fix it. 

Can anyone help identify what the problem is and how to solve it?
If you need anymore info i will try to do my best to provide it.
thanks for taking the time to read this.

attached is the results of running lshw in the terminal if it helps.
       

Thanks again

Update:
I just launched the other kernel 2.6.31-14 as apposed to 2.6.31-19 and the first run was very quick using the AWN.
Don't know what the difference is but its slow again for both.

---

### Post by mounty1512 on 2010-02-27
Problem solved. 
Everything is running really fast and smooth now.
If you have the same problem go [here]("http://friendlytechninja.com/2009/11/29/howto-fix-performance-of-ati-drivers-with-compiz-on-ubuntu-9-10-karmic-koala/").

If that site is down:
basically add *ppa*:launchpad-weyland/*xserver*-nobackfill to source list and run update manager.


Thanks
Loving Ubuntu now!

---

