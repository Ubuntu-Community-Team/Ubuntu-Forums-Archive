---
title: "Why can't ubuntu not manage it's swap space better?"
date: 2009-04-09
forum: General Help
---

### Post by jmate24 on 2009-04-09
Four Questions:

     i am wondering why Ubuntu, Kubuntu, etc. refuses to load my excess programs from memory into swap? 

     i have tried running Sound Juicer (Audio CD Extractor) to rip a CD and Sound Converter to Convert a 265.0GB MP3 Collection (about 1,500 songs at a time) to Ogg. But after i finish ripping my CD and when it automatically ejects the disk Sound Converter quits/crashes.

Does it have anything to do with both programs trying to use the same Gstreamer application at the same time?

If so, might they fix it in Jaunty? 

Because that would really help when i am trying to multitask.

I have a Dual Core 1.86GHz Processor (not Core 2, Bummmer!) Intel Laptop with 3GB RAM a 400GB HDD and 4GB Swap.

---

### Post by Stupendoussteve on 2009-04-09
Swap is meant to be used when memory is filled up. Windows has traditionally favoured swap over ram, but it has a negative impact on performance. If your ram is being used up, it will start swapping.

---

### Post by cariboo on 2009-04-09
Linux only uses swap when all the on board ram has been used up. It doesn't arbitrarily load prgrams to swap when there is still unused ram.

Jim

---

### Post by mb_webguy on 2009-04-09
+1

In other words, Linux is actually *smarter* in its use of swap than Windows.  A hard drive will *never* be as fast as memory.  As long as memory available, Linux will use it to ensure the best performance.

---

### Post by jmate24 on 2009-04-10
there is no more ram it uses the rest of the memory for cashe but the entire cashe does not get transfered only a few MB it does not even use hardly any ~0.01% and that is what puzzles me. i really think that it is a cashing problem i have checked my ram with memtest and still it closes down sound converter when i use sound juicer at the same time.

---

### Post by Ericyzfr1 on 2009-04-10
I saw a post on the Mandriva forum that had listed a command where it was possible to modify the ratio RAM/SWAP. You might want to look there if it can help with your issue.

---

### Post by mb_webguy on 2009-04-10
If you're talking about changing the swappiness of the system.  To do that, in the terminal, enter the command "gksu gedit /etc/sysctl.conf", add the line "vm.swappiness=10" at the end of the file, then save and exit. This value can range from 0 to 100, and the higher the number, the more your system will tend to write to swap instead of using available memory. A value of 0 means that swap will not be used. The default is 60.

However, most people who change the swappiness of their systems do so to *decrease* the systems' usage of swap in order to improve system performance.

---

### Post by Ericyzfr1 on 2009-04-10
Here is what I wrote down from it:

 edit: /etc/sysctl.conf

Last line vm.swappiness=60 (default) eg:changing to 80 will increase the use of swap memory.

To check the setting run:
cat /proc/sys/vm/swappiness

I believe by default ubuntu is also set to 60.

---

### Post by Slim Odds on 2009-04-10
jmate24, what makes you think there is a swap problem?

I think that you're way off base.

Do you think that Ubuntu servers that are very heavily loaded have swap problems?

P.S. Have you ever actually monitored what the memory usage is like during these operations?

---

### Post by jmate24 on 2009-04-10
it is just my laptop and i do think that changing my swappiness to 80 ~ 90 might do the trick.

thanks
jmate24--

---

### Post by jmate24 on 2009-05-04
i tried it and set it to 100 but then my laptop got too slow so i am going to try 90 and see if it is any better.


thanx for the input...

jmate24--

---

### Post by jmate24 on 2009-07-02
i have tried it both at 90 and 80 and i think that setting it to a lower value like 40 may do the trick..

thanx

---

