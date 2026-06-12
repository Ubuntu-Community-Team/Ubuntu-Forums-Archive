---
title: "Alpha Centauri Planetary Pack Crashes"
date: 2007-03-04
forum: Gaming &amp; Leisure
---

### Post by TheIdiotThatIsMe on 2007-03-04
I just recently got Alpha Centauri, Planetary Pack for Linux. Installation went off without a hitch, but when I try to run it, it works for a tiny bit then crashes with the following error:

Unable to create file: palcheck.tmp
Unable to create file: shadow.tmp
Unable to create file: spotlight.tmp
Unable to create file: reddish.tmp
Unable to create file: redtint.tmp
Unable to create file: bluetint.tmp
Unable to create file: fade.tmp
Unable to create file: colorvals.tmp
Unable to create file: explosions0.tmp

BUG! (Segmentation Fault)  Going down hard...
Sid Meier Alien Crossfire 6.0 Linux
Built with glibc-2.1
Stack dump:
{
        [0x8375dad]
        [0xffffe420]
        [0x82d26ef]
        [0x81d2ae6]
        [0x824b0e3]
        [0x82e6c06]
        [0x8448ecd]
        [0x8048111]
}

---

### Post by fyd on 2007-03-08
> **TheIdiotThatIsMe said:**
> I just recently got Alpha Centauri, Planetary Pack for Linux. Installation went off without a hitch, but when I try to run it, it works for a tiny bit then crashes with the following error:

Unable to create file: palcheck.tmp
Unable to create file: shadow.tmp
Unable to create file: spotlight.tmp
Unable to create file: reddish.tmp
Unable to create file: redtint.tmp
Unable to create file: bluetint.tmp
Unable to create file: fade.tmp
Unable to create file: colorvals.tmp
Unable to create file: explosions0.tmp

BUG! (Segmentation Fault)  Going down hard...
Sid Meier Alien Crossfire 6.0 Linux
Built with glibc-2.1
Stack dump:
{
        [0x8375dad]
        [0xffffe420]
        [0x82d26ef]
        [0x81d2ae6]
        [0x824b0e3]
        [0x82e6c06]
        [0x8448ecd]
        [0x8048111]
}

This is a known glibc problem with Alpha Centauri. There is a patch somewhere out there in the world wide web, try to google for it. If i find it, I'll tell you. Alternatively you can use old libraries as described here: 
[http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games](http://gentoo-wiki.com/HOWTO_Running_Old_Loki_Games)


But bad new for you: After solving the glibc problem, you will most probably find out that it still does not work: [http://www.ubuntuforums.org/showthread.php?t=298679&highlight=alpha+centauri](http://www.ubuntuforums.org/showthread.php?t=298679&highlight=alpha+centauri)

I'm trying to solve this problem at the moment though.

---

