---
title: "Dell Photo AIO 926 Printer"
date: 2007-08-07
forum: Dell  Ubuntu Support
---

### Post by MidChaos on 2007-08-07
Greetings!

Well, I guess my largest issues are always printers, everything else I always get worked out. Anyway, here is the scoop on this problem I am having (and I hope we can find success, you'll see why).

Anyway, a family member of mine got a new Dell laptop pre-installed with Vista. After a short amount of time (about 2 weeks or so) they decided that they do not like Vista and let me install Ubuntu on it. I found lots of easy support to get the graphics card running and the wireless (hooray for these forums!). Then I got to the printer (which, ignorant me thought would work because it saw the model, oh well, next time I'll know better) that is the model that I have named this post after. Sadly, like many, I am lacking support for this printer. I can't even tell which Lexmark it is similar to to work from there.

Anyway, I am hoping that someone might have some things for me to try to get it to work (this could be a converted computer permanently if I can get it to work). I tried various different drivers, including the z600 which didn't work. It almost responded with the z53, it said printing, the machine made noises, then nothing (Ubuntu continued to say it was printing). Is it possible one of the generic printer drivers would work? Any advice on this would be great, it'll be a bit before I can get back to the location to try anything, but the gathering of knowledge and ideas is what I'm after here.

Thanks in advance!

P.S. Sorry if I'm lacking information, please let me know what else you might need from me as far as what I've tried.

---

### Post by softdel on 2007-09-05
I think that Dell should make a driver for their printer, even if it can only print. This is a nightmare situation from dell. 

C'mon guys, get your backsides in gear, us Ubuntu users want out printers to work!

---

### Post by brundlelinux on 2007-10-14
I am also having "Dell" printer issues.  After a few hours of research, I've come across most of the same information as the original poster.  A "Dell" printer is nothing but a rebranded Lexmark dressed up for Halloween in a Dell costume.

Traditionally, Lexmark, as a company, has NOT embraced open-source or Linux and guards their proprietary driver technology under strict lock and key.  This, in turn, prevents Dell from offering support for "Dell" printers.

As the second poster mentioned, this is a nightmare situation for Dell.  I can't imagine how this seemed like a good idea when brought up in a Dell boardroom meeting among the "suits."  Especially considering that Dell has "officially" taken a position as "supportive" of Linux by offering to ship new systems out with Linux pre-installed instead of Windows.

As far as I'm concerned, it's like going to eat dinner in restaurant and ordering steak, only to find out afterwards that they will not provide you with forks or a steak knife, and the steak sauce is an extra $250 dollars a bottle.

---

### Post by softdel on 2007-10-14
> **brundlelinux said:**
> I am also having "Dell" printer issues.  After a few hours of research, I've come across most of the same information as the original poster.  A "Dell" printer is nothing but a rebranded Lexmark dressed up for Halloween in a Dell costume.

Traditionally, Lexmark, as a company, has NOT embraced open-source or Linux and guards their proprietary driver technology under strict lock and key.  This, in turn, prevents Dell from offering support for "Dell" printers.

As the second poster mentioned, this is a nightmare situation for Dell.  I can't imagine how this seemed like a good idea when brought up in a Dell boardroom meeting among the "suits."  Especially considering that Dell has "officially" taken a position as "supportive" of Linux by offering to ship new systems out with Linux pre-installed instead of Windows.

As far as I'm concerned, it's like going to eat dinner in restaurant and ordering steak, only to find out afterwards that they will not provide you with forks or a steak knife, and the steak sauce is an extra $250 dollars a bottle.

Haha, I have to agree. Why are lexy so pi*sy about releasing their drivers, they aren't exactly going to help anyone steal their printers.

---

### Post by brundlelinux on 2007-10-15
I just want to add that there **is** a workaround for this problem with non-supported printers on Linux.  Obviously, this solution won't work so well in the given conditions of the original post with this being for a distant family member, but...

If you have a dual boot machine running Linux and Windows, you can set up your Ubuntu to mount the Windows partition and route your print commands through the windows partition, pick up the support from the embedded Windows driver, and print using the Windows based partition as your print engine.  Obviously, this requires a legal copy of Windows running on your machine and a fair amount of scripting and coding.  If I'm not mistaken, it also involves translating the printer command output into a PDF generic reader which then does some kind of magical technology translation and enables the printer to work.

I'm a newbie and have no clue what that is all about.... but search it out in the forums if you're better at this whole Linux "under the hood" thing than I am.

Good luck!

---

