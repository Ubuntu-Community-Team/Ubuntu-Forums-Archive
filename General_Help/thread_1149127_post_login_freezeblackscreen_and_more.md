---
title: "post login freeze/blackscreen and more"
date: 2009-05-04
forum: General Help
---

### Post by hilo4321 on 2009-05-04
Hello all,

I've been using ubuntu since about 6.10, so while my time here may not reflect it, I have pretty good familiarity with it.  Anyway, a while back, ubuntu (on my PC) just outright stopped working.  I dual boot, and essentially just boot into windows to play games (and use chrome), and sometimes just get real lazy, and don't boot back into ubuntu for a while.  In any case the reason I'm telling you this, is because sometime in the past few months, my install of 8.10 just plain stopped working.  It would reach the login screen most of the time (sometimes freeze at it), but after login (1-15 seconds) it would hard freeze with no input at all, no mouse, not even numlock.  This frustrated me quite a bit, and after much screwing around I just gave up outright, which is a rarity for me, and especially since I love ubuntu.  My interest in it came back, so i figured ok, I'll just wipe it clean and install 9.04, and I'll be problem free.  Boy was I wrong.  I couldn't even install it.  Essentially the same problem would happen when trying to install.  So i grabbed the alternate cd and it installed.  Lo and behold, same login problem.  I have been looking for days to find a way to fix this problem, to no avail.  Here is what I have done:

-noacpi, noapm, noapic options
-tried taking out the 3rd (1gb) stick of ram
-booting into failsafe graphics/terminal
-I deleted compiz/compiz-core (sp?)
     *made new problem, went to black screen with mouse movable
-probably 5 other things that I can't remember

questions:

-could it be because I am installing 32bit onto AMD64?
     *I really don't want to mess with 64 bit
-could it be graphics problems?
     *I have an 8600gts
     *xorg.conf only contains input stuff (this is apparently by design now? I don't know.)
     *dpkg-reconfigure xsession-xorg(can't remember if that's right) asks no questions about graphics (by design?)

I have:

-AMD Athlon 64 X2 5000+
-Gigabyte M57SLI-S4 motherboard
-2 GB OCZ PC2-6400
-1 GB Corsair PC2-6400
-EVGA 8600gts 
-Ubuntu HD - 80GB ATA (ext3)
-Windows/storage HD 300GB SATA (ntfs)
-Storage HD 1TB INOI external (fat32)

Also, every time I install Ubuntu, grub gives me error 13 when I try to get into windows, and I never remember what I did the last time I installed so I have to spend 3 hours figuring it out again.  It's real annoying.  Different topic for different day.

I just want this to work!  I've converted 3/5 roommates to it in the last year, and I think I have more problems with it than any of them.  Which is good, because they would probably give up after much less time than me. :P

Thanks for your help in advance, and if I left some important info out let me know.

EDIT: I tried to use whitespace, but it didn't work, so now * = indent

---

