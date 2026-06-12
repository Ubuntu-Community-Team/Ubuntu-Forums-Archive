---
title: "Compiz Install"
date: 2011-02-02
forum: Desktop Environments
---

### Post by SM95 on 2011-02-02
Hi people!! Since I start using Ubuntu, I tried to use special effects, but with no sucess. Going into forums I read that for my graphic card, I should totally forget about it.
 Time passed, and I watch a video on YouTube [http://www.youtube.com/watch?v=Hklpe0OCclg]("http://www.youtube.com/watch?v=Hklpe0OCclg") where an user could finally get to do it.
 New hopes, I ran new how-to and guides but I get to a point where all the results in searchs are related to older versions of ubuntu (I've 10.04, so the xorg file doesn't exist).
 The error is "Software Rasterizer in use" of the compiz-check script [http://forlong.blogage.de/entries/pages/Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check")
 Info:
 Ubuntu 10.04
 Graphic Card: VIA S3G Unichrome Pro 64mb (which seems to be detected)
 Processor: Intel Pentium IV 2.66 Ghz
 RAM: 448mb

 Hope you can give some help.
 Thank You.

---

### Post by Frogs Hair on 2011-02-02
Is there a proprietary driver for your graphicis chip/card ? To find out go to System > Administration > Additional Drivers / Hardware and Drivers.
 
Are desktop effects enabled ? To do so go to Appearence Preferences > Desktop Effects tab and set to normal. 
 
Some graphics cards / chips are black listed and don't work with Compiz . there is Ubuntu community documentation and a list of affected cards/ chips. I don't have the link handy , so do a search.

---

### Post by Forlong on 2011-02-02
Please post the complete output of compiz-check.

Did you install any driver? The guy on Youtube claims you need to download one directly from Via.

Please note that video is two years old, so there has been a lot of development since then.
For example, there is no easy way, that I'm aware of, to make Compiz run on blacklisted hardware in a current install of Ubuntu.
So unfortunately, even if it would be possible to run Compiz on your hardware, it will involve additional hassle to make it work on Ubuntu.

You have to decide for yourself if it would be worth it.

---

### Post by Copper Bezel on 2011-02-02
Seriously? SKIP_CHECKS=yes doesn't work anymore? Editing the configuration files doesn't work? If so, that's damned troubling, simply idiotic on the part of the devs. It's not as if the blacklist means anything relevant to stability. I've had exactly as *few* and exactly as *many* problems with Compiz on the two machines I've used it on, exactly one of which was blacklisted.

---

### Post by Forlong on 2011-02-02
Changes regarding Compiz have always been very poorly documented, mostly not at all. So I'm not quite sure what the current status regarding blacklisted hardware is. I will have to look into this.

But yes, since the wrapper script and the compiz binary are not separate in Ubuntu anymore, the SKIP_CHECKS variable is not read by anything.

---

### Post by SM95 on 2011-02-02
Well, I agree with you all, the documentation is poor, there were a lot of changes among the last versions of ubuntu, and the most of us doesn't know how to do what we used to with old tools.
 Anyway, As There is more documentation of older distros, and I won't be loosing so much doing it, I will return to Ubuntu Hardy Heron, as a recomendation of another ubuntu user witch similar pc specifications.
 Thanks a lot for the help.

---

