---
title: "Why everything on my machine is slowing down each day?"
date: 2009-05-15
forum: General Help
---

### Post by jeremieducharme on 2009-05-15
Last winter, I gave a try to Ubuntu on my Pentium 4 (512mo RAM). It was ok 'til it starts to slow down more and more each day. Starting and using applications, such as Firefox, Audacious, the ones on Wine, browsing files on my usb stick, everything get sluggish. I tested my stick on a Windows machine and it worked just fine. The CPU usage seems ok. At this time, I installed the version 8, but I am not sure to go with the 9, if it is all that messy and/or I have to reinstall the OS. Why everything on my machine has slowed down and continue that way?

---

### Post by kahootbot on 2009-05-15
That is such a general problem all I can offer are general suggestions.. 

Try to look for hints from specific applications such as Firefox. I've heard some extensions to firefox have memory leaks for example.

In general, try to be mindful of what you have open at one time. 512 memory should be plenty, but with any amount of memory to much open at one time could make things go to paged memory. Paged memory is memory stored on the hard drive, and is much slower than normal memory because of the input/output..

Some USB drives do indeed perform faster than others, so you might check which one you are plugging your USB stick in when browsing..

Use the "top" command and keep an eye on your memory/cpu usage if you have a lot of applications open at once. There has to be a reason they are going slower. 

you might make sure your the only user logged in, and consider getting a firewall if you don't have one.

-kahootbot

---

### Post by AXeS on 2009-05-15
i got a similar problem...

i got a AMD 64 2.4Gig processor 2.5gigRAM,i installed 8.10 on my 80gig. my kuz g0ta DUAL CORE AMD 2GIG and 2gigRAM and have 8.10 on a 40gig parti0n.

now i g0ta sl0w net c0nnecti0n n he d0nt have...we d0wnloaded and installed c0decs 4 b0th the b0xes. problem is...he just g0t c0decs and i g0ta al0ta pr0gramz installed...his pc glitches/skips/slow perf0rmance. 0n my pc 0nly the vide0 gives me that pr0blem.

i asked before and got no valid repsonse.so now i wana know ,what gives?

btw,this is 0ur 3rd install each...hardware worx fine,no 0tha problems.

---

### Post by wpshooter on 2009-05-15
Is it possible that you just need to clean up your hard drive ?

---

### Post by Tipped OuT on 2009-05-15
> **AXeS said:**
> i got a similar problem...

i got a AMD 64 2.4Gig proce55or 2.5gigRAM,i installed 8.10 on my 80gig. my kuz g0ta DUAL CORE AMD 2GIG and 2gigRAM and have 8.10 on a 40gig parti0n.

now i g0ta sl0w net c0nnecti0n n he d0nt have...we d0wnloaded and installed c0decs 4 b0th the b0xes. problem is...he just g0t c0dec5 and i g0ta al0ta pr0gram5 installed...his pc glitches/skips/slow perf0rmance. 0n my pc 0nly the vide0 gives me that pr0blem.

i asked before and got no valid repsonse.so now i wana know ,what give5?

btw,this is 0ur 3rd install each...hardware worx fine,no 0tha problem5.

1337... :neutral:

---

### Post by stinger30au on 2009-05-15
do the basics first

clean out the fans with compressed air

check the hard drive for bad sectors

something like [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) will do the trick

---

### Post by AXeS on 2009-05-16
> **Tipped OuT said:**
> 1337... :neutral:

I dont get what you speaking,i dont talk num0r0n.
 
as for wpshooter,my 3rd install being not using wubi n n0 partiti0ns.as for the programs,i just installed the c0decs 1st...coupla days later it started lagging s0 i thought skrew-it im not gona re-install again.
and the same with my kuz,he got glitches just paging through a pdf magazine.
i checked both the HDD before we installed it on a full HDD and i got a agp graphics card ATI radeon 9550 (dont tell me its because of that)
koz my kuz got nvidia 7200.
The usual box clean-out works great for windows but i dont wana be in windows.
im a fan of linuy and i asked around about ubuntu an people just give off bad comments saying its good if you wana learn bash but practicaly the gui is a front.
im starting to believe that,i dont mind the terminal at all,i think its super-cool,but if i wana put ubuntu 0n my sisters pc then i gota show her some stratergies.

im sure i could get to fix the problemz i have through the terminal but im yet t0 discover how.

---

### Post by hyperdude111 on 2009-05-16
> **jeremieducharme said:**
> Last winter, I gave a try to Ubuntu on my Pentium 4 (512mo RAM). It was ok 'til it starts to slow down more and more each day. Starting and using applications, such as Firefox, Audacious, the ones on Wine, browsing files on my usb stick, everything get sluggish. I tested my stick on a Windows machine and it worked just fine. The CPU usage seems ok. At this time, I installed the version 8, but I am not sure to go with the 9, if it is all that messy and/or I have to reinstall the OS. Why everything on my machine has slowed down and continue that way?

I also had poor performance on a pentium 4 machine with 512 mb of RAM.

On my new machine i no longer have these problems. Good luck

---

### Post by HuckleSmothered on 2009-05-16
Too much internet porn, all of you.

---

### Post by rpwdh on 2009-05-16
> **wpshooter said:**
> Is it possible that you just need to clean up your hard drive ?

[Here's a great tutorial](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by oldsoundguy on 2009-05-16
Maybe a HARDWARE stress test is in order?

Ultimate Boot disk or Hiren's Boot CD and run a bank of tests on the processor, memory, whatever. (both free for downloading and burning.)

We almost always blame the software when stuff starts going south .. and SOMETIMES are right.  But elimination of any hardware issues assures that we are on the right track.

I had an issue recently where the SECOND memory stick went south .. so when I got a memory call and it required going to the second stick, all KINDS of problems. Removed it, sent it to Kingston on an RMA,  got the free replacement, put it in and the box works flawlessly.

---

### Post by FIONEX on 2009-05-16
it's possible that your computer is just physically failing.  Over time, the processor and ram start to wear down due to high temperature and other factors.  Some computers slow down to a halt from being under stress at all times.  Servers usually don't last more than 2 years before they start slowing down and causing errors.

---

### Post by AXeS on 2009-05-17
hey thanx, oldsoundguy and FIONEX... that sounds logical,i got my box for 3years now,but for a box that was bought 3months ago...im guesing it eliminates that or what yall say?

---

### Post by FIONEX on 2009-05-18
if a box that you have is only 3 months old then I would diagnose what's up.  If ubuntu is running slow, I would run some tests.

From the sounds of it, your RAM might be failing...  Reboot and when you get to GRUB, run a memtest and let it go for 30 minutes.

I would also run the command "top" to see what's hogging resources.  Then I would run benchmarks to test the harddrive read/write speed or the CPU calculation performance or the ram read/write/invert speed.


Sometimes, certain hardware drivers don't work well with your specific hardware, and they start hanging.  So I would start by removing certain modules that aren't necessary by doing "sudo rmmod snd" to remove all the sound drivers and see if that changes anything.  You can type "lsmod" to see what modules are loaded.

Good luck with that!

---

### Post by AXeS on 2009-05-19
> **FIONEX said:**
> if a box that you have is only 3 months old then I would diagnose what's up.  If ubuntu is running slow, I would run some tests.

From the sounds of it, your RAM might be failing...  Reboot and when you get to GRUB, run a memtest and let it go for 30 minutes.

I would also run the command "top" to see what's hogging resources.  Then I would run benchmarks to test the harddrive read/write speed or the CPU calculation performance or the ram read/write/invert speed.


Sometimes, certain hardware drivers don't work well with your specific hardware, and they start hanging.  So I would start by removing certain modules that aren't necessary by doing "sudo rmmod snd" to remove all the sound drivers and see if that changes anything.  You can type "lsmod" to see what modules are loaded.

Good luck with that!


been busy but i'll check tonight...i think it could be updates that are needed? or what you think?

---

### Post by FIONEX on 2009-05-20
Yeah, an update might install newer drivers/modules...Do the tests as I suggested.  Start with Mem test, then do a CPU stress test, then a harddrive stress test.  I know that the xorg in ubuntu 9.04 was slow on ATI video cards.  I had to get a patched xorg in order for it to be fast.

---

