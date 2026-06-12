---
title: "motherboard clock doesn't keep time."
date: 2006-01-09
forum: General Help
---

### Post by bannerboy on 2006-01-09
My motherboard clock doesn't keep good time, and I cant get ntpd working. my computer syncs fine with the kubuntu time server but I can't get ntpd working to keep the time right.

---

### Post by Efwis on 2006-01-09
this could be caused by the battery on your motherboard dying.

---

### Post by bannerboy on 2006-01-09
highly unlikely, my motherboard is 3 weeks old.

---

### Post by Efwis on 2006-01-09
[QUOTE=bannerboy]highly unlikely, my motherboard is 3 weeks old.[/QUOTE]
and it was on the shelf with the battery in it for how long before you bought it?? or for that matter the battery was made when???

I guess the point I'm making is, it doesn't matter how hold you mobo is. I have bought brand new batteries taken them out of the packaging and found them dead. As well as other computer components. I would recommend checking that if you have a spare battery around per chance. even manufacturers get bad parts occasionally from their suppliers.

---

### Post by earobinson on 2006-01-09
Ohh I havent seen a post like this in a while, do you dual boot, did you just install linux? if so:
[http://www.ubuntuforums.org/showthread.php?t=87649](http://www.ubuntuforums.org/showthread.php?t=87649)
[http://www.ubuntuforums.org/showthread.php?t=71720&highlight=time+windows](http://www.ubuntuforums.org/showthread.php?t=71720&highlight=time+windows)

hope that helps

EDIT ohhh i also found this [http://ubuntuforums.org/showthread.php?t=75281](http://ubuntuforums.org/showthread.php?t=75281)

---

### Post by bannerboy on 2006-01-09
no, I just run linux. I've had similar problems with other computers, but I've never had a motherboard clock this bad. I'll check the battery, and we'll take it from there.

EDIT: I just checked the battery, and it's a lithium, so I doubt that its bad.

---

### Post by Efwis on 2006-01-09
i also did some further researching on this.

>  to protect against broken hardware, such as when the CMOS battery fails or the clock counter becomes defective, once the clock has been set, an error greater than 1000s will cause ntpd to exit 

---

### Post by feathers on 2006-01-09
Do you really use ntpd? Because to synchronise the time you need ntpdate. Another thing that might help is to look at hwclock which set the time and corrects the deviation from the correct time.

---

### Post by bannerboy on 2006-01-09
ntpdate sets the time once, when you boot up your computer. but my motherboard clock os fast, and ntpd is capable of constantly updating your time so that it is always correct.

---

### Post by MorayJ on 2007-05-06
> **feathers said:**
> Another thing that might help is to look at hwclock which set the time and corrects the deviation from the correct time.

I don't know if anyone is still watching this thread so may start a new post.

There is something seriously weird with the clock and a lot of people are suggesting that it's CMOS (BTW I'm running PPC on a Mac-Mini, so don't know if this is related to that so maybe not everyone's problem).

It's not the CMOS. I installed OSX and ran that for a while and it kept time perfectly.

I just tried hwclock as suggested above, and it gives the right time!

So can anyone explain why the system time is off (it is off in the clock in gnome and it is also off when you create files etc.)?

Cheers
Moray

---

