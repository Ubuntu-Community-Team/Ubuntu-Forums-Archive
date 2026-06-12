---
title: "Fedora 9&gt;Hardy Heron"
date: 2008-05-25
forum: Fedora/RedHat and derivatives
---

### Post by quadomatic on 2008-05-25
I've been using Ubuntu for years now. Every time I've tried another distro, I've always come back to Ubuntu. But with Hardy Heron, I've absolutely had it. Kernel panics related to wireless drivers were being complained about since the beta, and yet nothing was done to fix them. Once the final release came out, I couldn't even connect to the internet anymore. Gutsy Gibbon had wireless problems for me as well, but I was still able to use ndiswrapper. That wasn't doable on Hardy.

Fedora 9 has everything that I loved about Ubuntu. Packages are easy to get. Everything just works. ATI works fantastically (once you work around the problems with the kernel not being supported by the drivers, very easy) and is much faster than in Ubuntu.

Here's the guide for getting around the ATI driver incompatibility. It's easier than updating ATI drivers in Ubuntu:

[http://forums.fedoraforum.org/forum/showthread.php?t=189227](http://forums.fedoraforum.org/forum/showthread.php?t=189227)

I will say that it was much more difficult to get all the codecs and stuff installed, but then I found this guide:

[http://www.my-guides.net/en/content/view/103/26/](http://www.my-guides.net/en/content/view/103/26/)

This is helpful too. Its similar to Automatix.

[http://easylife.dulinux.com/](http://easylife.dulinux.com/)

So for those of you disgruntled by Hardy, go ahead and give Fedora 9 a try. You won't regret it.

---

### Post by Twitch6000 on 2008-05-25
> **quadomatic said:**
> I've been using Ubuntu for years now. Every time I've tried another distro, I've always come back to Ubuntu. But with Hardy Heron, I've absolutely had it. Kernel panics related to wireless drivers were being complained about since the beta, and yet nothing was done to fix them. Once the final release came out, I couldn't even connect to the internet anymore. Gutsy Gibbon had wireless problems for me as well, but I was still able to use ndiswrapper. That wasn't doable on Hardy.

Fedora 9 has everything that I loved about Ubuntu. Packages are easy to get. Everything just works. ATI works fantastically (once you work around the problems with the kernel not being supported by the drivers, very easy) and is much faster than in Ubuntu.

So for those of you disgruntled by Hardy, go ahead and give Fedora 9 a try. You won't regret it.

I am a big distro hopper and well when I tried fedora 9 it had more bigs then hardy did.It did not like my webcam or my wireless,unlike hardy.Plus something about what came with it makes it not compatible with the ;atest nvidia cards.

---

### Post by Playa1313 on 2008-05-25
I agree that Fedora 9 is very compatible with many things (ie. my suspend/hibernate works when in Hardy it doesn't)

However, I did find it quite annoying that the kernel and xorg weren't even supported by the ATI drivers when it was released.  This is what led me away from Fedora 9, but _does not_ mean I will not return when this is worked out.  

I know you mentioned a fix for it, but I think that's kind of a stretch - especially for beginning users who might be trying Linux for the first time and looking for that awesome desktop cube or sphere they saw on youtube.  They can't use that without the driver.

Thanks,
Brian

---

### Post by quadomatic on 2008-05-25
> **Playa1313 said:**
> I agree that Fedora 9 is very compatible with many things (ie. my suspend/hibernate works when in Hardy it doesn't)

However, I did find it quite annoying that the kernel and xorg weren't even supported by the ATI drivers when it was released.  This is what led me away from Fedora 9, but _does not_ mean I will not return when this is worked out.  

I know you mentioned a fix for it, but I think that's kind of a stretch - especially for beginning users who might be trying Linux for the first time and looking for that awesome desktop cube or sphere they saw on youtube.  They can't use that without the driver.

Thanks,
Brian

[http://forums.fedoraforum.org/forum/showthread.php?t=189227](http://forums.fedoraforum.org/forum/showthread.php?t=189227)

Here's the guide I used to get around the kernel problems. It was very easy.

Honestly, I think its easier than updating ATI drivers in Ubuntu.

---

### Post by Playa1313 on 2008-05-25
> **quadomatic said:**
> [http://forums.fedoraforum.org/forum/showthread.php?t=189227](http://forums.fedoraforum.org/forum/showthread.php?t=189227)

Here's the guide I used to get around the kernel problems. It was very easy.

Honestly, I think its easier than updating ATI drivers in Ubuntu.

Honestly, I saw that guide before, but did not know if that was pre-ATI 8.5 release or not.  I was actually about to work on installing the ATI driver, but ran into some problems with my partitions.  I installed XP and it completely messed up my partition table, killing the Fedora partition <.<.  But like I said, I have no reasons for not installing it again if I get that working :D.

---

### Post by quadomatic on 2008-05-26
> **Playa1313 said:**
> Honestly, I saw that guide before, but did not know if that was pre-ATI 8.5 release or not.  I was actually about to work on installing the ATI driver, but ran into some problems with my partitions.  I installed XP and it completely messed up my partition table, killing the Fedora partition <.<.  But like I said, I have no reasons for not installing it again if I get that working :D.

I know exactly what you mean with XP destroying partition tables. I lost an entire partition of photos and music because of that once. The old XP install cds don't recognize linux partitions. Newer XP cds work though.

---

### Post by fyrestrtr on 2008-05-29
Fedora 9 also comes with the new network manager with support for GSM cards; something lacking in Hardy.

Generally, Fedora is quicker out the gate with new/updated releases than Ubuntu.

I just now switched from F9 to Ubuntu, my personal reasons:

1. Hate rpm/yum -- love apt
2. SELinux and the annoyances associated with it.
3. Can't install drivers for my video card (nvidia) = slow scrolling in Firefox which is causing me grief on my 15" laptop.
4. Mysterious hanging with high disk usage -- never before seen on any other distro (including F8).

What I really wish Ubuntu would have:

1. Updated theme from the orange / brown. Really its getting quite old. I love the Fedora theme and will be installing it once this update is done.

2. Update network manager to support GSM cards.

3. Employ the very nice and professional looking startup screen in Fedora. Anyone knows how to get that going? It is one of the best features of Fedora. Its a lot better than the very ugly bar in Ubuntu, which provides no useful information.

---

### Post by PmDematagoda on 2008-05-29
> **fyrestrtr said:**
> What I really wish Ubuntu would have:

1. Updated theme from the orange / brown. Really its getting quite old. I love the Fedora theme and will be installing it once this update is done.

2. Update network manager to support GSM cards.

3. Employ the very nice and professional looking startup screen in Fedora. Anyone knows how to get that going? It is one of the best features of Fedora. Its a lot better than the very ugly bar in Ubuntu, which provides no useful information.

1) The theme will be revamped in Intrepid.

2) Network Manager 0.7(which brings all that magic) will be included in Intrepid.

3) It's a different splash screen from Ubuntu which uses usplash, Fedora uses RHGB, but who knows what may happen in Intrepid:).

---

### Post by ZuLuuuuuu on 2008-05-29
Fedora 9 > Hardy is a bit arguable. But what not arguable is that Fedora comes closer to Ubuntu in every release and with Fedora 9 that distance has become quite smaller.

---

### Post by cardinals_fan on 2008-05-29
> **PmDematagoda said:**
> 
2) Network Manager 0.7(which brings all that magic) will be included in Intrepid.

Why is Network Manager still used?  It has traditionally been a horribly couterintuitive program, and Wicd is much better.

---

### Post by PmDematagoda on 2008-05-29
> **cardinals_fan said:**
> Why is Network Manager still used?  It has traditionally been a horribly couterintuitive program, and Wicd is much better.

Perhaps to you, but there are enough people who use NM and find it to be very good. The only difference between NM and Wicd is that Wicd uses more drivers, yet even this is not that much of an advantage since the extra drivers that Wicd has are unstable or rather risky to use for general purposes.

Just give Network Manager 0.7 a try, you may be impressed:).

---

### Post by Istonian on 2008-05-29
I would use F9, but they decided to use the newer Xorg that does not have nVidia driver support. I need my 3d. And since Hardy has been amazing for me. No reason to switch.

---

### Post by Novega on 2008-05-29
> **Istonian said:**
> I would use F9, but they decided to use the newer Xorg that does not have nVidia driver support. I need my 3d. And since Hardy has been amazing for me. No reason to switch.

Doesn't the new Nvidia Driver that was released yesterday (or the day before) work for Fedora 9? 
[LIST]
[*]Added preliminary support for X.Org server 1.5.
[/LIST]

I wasn't entirely sure what the problem was with Nvidia and F9 but I downloaded it, burned it and never installed it b/c I heard there were issues.

---

### Post by Antman on 2008-05-30
> **Novega said:**
> Doesn't the new Nvidia Driver that was released yesterday (or the day before) work for Fedora 9? 
[LIST]
[*]Added preliminary support for X.Org server 1.5.
[/LIST]

I wasn't entirely sure what the problem was with Nvidia and F9 but I downloaded it, burned it and never installed it b/c I heard there were issues.
I just saw the nVidia post on their site and was going to install f9 again on my desktop (which currently has Ubuntu installed since I need to use nVidia drivers for dual screens mode). Maybe I will test it later tonight.

---

### Post by ingvildr on 2008-06-02
> **fyrestrtr said:**
> Fedora 9 also comes with the new network manager with support for GSM cards; something lacking in Hardy.

Generally, Fedora is quicker out the gate with new/updated releases than Ubuntu.

I just now switched from F9 to Ubuntu, my personal reasons:

1. Hate rpm/yum -- love apt
2. SELinux and the annoyances associated with it.
3. Can't install drivers for my video card (nvidia) = slow scrolling in Firefox which is causing me grief on my 15" laptop.
4. Mysterious hanging with high disk usage -- never before seen on any other distro (including F8).

Can i ask what exactly is your problem with yum/rpm and selinux?

---

