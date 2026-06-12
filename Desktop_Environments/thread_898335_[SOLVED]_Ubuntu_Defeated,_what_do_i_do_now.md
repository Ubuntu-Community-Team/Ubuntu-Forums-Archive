---
title: "[SOLVED] Ubuntu Defeated, what do i do now?"
date: 2008-08-23
forum: Desktop Environments
---

### Post by ntbutler on 2008-08-23
Hi all.

I am in a bit of a jam. I have been thoroughly convinced windows is evil, but however i still need it for some things. My plan was to upgrade my pc (from a p3 256mb ram dino), then install ubuntu and run windows in vmware.

My problem is this. I have purchased a Gigabyte GA-P45-DS3P motherboard, (also a pentium core 2 quad processor and GeForece 8800GT gc), and it seems ubuntu is defeated when it comes to installing...

I have tried 7.10, 8.04.1 and 8.04 PC User Extreme OS edition and none of them will install.

In a previous post of mine today [http://ubuntuforums.org/showthread.php?t=898177](http://ubuntuforums.org/showthread.php?t=898177) i was told that this was because the p45 chipset isn't supported.

I am feeling a little defeated about this, so i was wondering if anyone knew of any ubuntu derivatives that would support my mb, or of any other linux distributions anyone would like to reccommend.

Thanks all :)

---

### Post by stinger30au on 2008-08-23
there is plenty of forks of Ubuntu

here is few here

[http://en.wikipedia.org/wiki/List_of_Ubuntu-based_distributions](http://en.wikipedia.org/wiki/List_of_Ubuntu-based_distributions)

hope this helps

---

### Post by Lazy79 on 2008-08-23
i do not think this is distribution-related.. is there not failure message/log..?

---

### Post by ntbutler on 2008-08-23
Hey all.

Yeah, i have been looking at the problem and i don't think it is a distro problem, it was just something the guy said in that other thread i posted about the p45 chipset not being supperted by the kernel, that it had to be in a 2.6.25-26 kernel, so i was just seeing if anyone knew of an easy option.

The thing is, i have tried 6.10, 7.10, 8.04.1 and 8.04 Extreme OS and they all end up doing the same thing (6.10 was a little different, but pretty much same story).

The specs of my computer were:
[LIST]
[*]Gigabyte GA-EP45-DS3P motherboard
[*]Intel Core 2 Quad processor
[*]GeForce 8800GT Graphics card
[*]2GB RAM
[*]80GB SATA HDD
[/LIST]

The weird thing is that i tried the Mandriva 2007 liveCD and it got to the blue GUI screen with only the mouse (further than ubuntu got), but then i tried an old version of knoppix, i think version 3.7, which booted fine.

I hate to be reposting this stuff from the last thread, but it is just weird, I have looked at other threads including the problem i was getting, but nothing that really helped.

Anyway, if anyone has any ideas, that would be great, otherwise i am going to put up with windows for the next few weeks to do my assignments, then try again...

:)


EDIT: Sorry, forgot to mention, i couldn't find any error log, as i said in the other thread, it just said loading, please wait on one terminal, and then had the busybox initramfs prompt on another, thats all (I am working straight off the CD with a blank HDD so i wasn't getting any error outputs or error logs)

---

### Post by ntbutler on 2008-08-23
Just thought i'd mention, i have now installed windows on the HDD, which boots fine, but i have no network :(. I miss ubuntu...

---

### Post by clueless on 2008-08-23
The second beta of Mandriva 2009 is out, you could try and see from the live DVD if your motherboard is supported and maybe try it out.

x86_64 mirror:
[ftp://ftp.free.fr/mirrors/ftp.mandriva.com/MandrivaLinux/devel/iso/2009.0/beta2/mandriva-linux-free-2009-okapi-dvd-x86_64.iso](ftp://ftp.free.fr/mirrors/ftp.mandriva.com/MandrivaLinux/devel/iso/2009.0/beta2/mandriva-linux-free-2009-okapi-dvd-x86_64.iso)

---

### Post by ntbutler on 2008-08-24
SOLVED!!!
After combing ubuntu forums for the last 2 days I found someone who said that they had problems similar and changed the bios settings for the Sata to be raid. I am not running raid, but it worked, so now i am typing this on my newly installed 8.04 Extreme OS.
Hope this makes things easier for anyone else with siwilar problems.

If you are using a SATA board, try switching the SATA bios settings to raid (just one thing, but helped alot)!

Happy again!

---

