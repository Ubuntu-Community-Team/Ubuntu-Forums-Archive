---
title: "_very_ lightweight install"
date: 2007-03-21
forum: Debian
---

### Post by Big_Croc7 on 2007-03-21
Hi, I'm looking at setting up an old 486 system to XDMCP into a fast(ish) Ubuntu box.

I think this is right: I need to enable remote logins (from System/Admin/Login Window or something), and all I need on the old box is an install with an Xserver and networking, right?

Can anyone recommend a distro for the client PC? It's a 486 with 8Mb RAM and a 180Mb HD; I was thinking of using a Debian absolute minimal install (from floppy disk) and getting just the absolute minimum packages for an Xserver.  Any comments?

cheers! :)

---

### Post by mips on 2007-03-21
DSL, Puppy etc Have a look here as there has been many similiar threads.

---

### Post by Cyvros on 2007-03-21
From what I've heard, Arch Linux might fit your bill, but I'd go for DSL.

---

### Post by Kindred on 2007-03-21
Arch is i686 optimised, there is a version for older machines put together by a user but perhaps not worth the hassle.  

I would likely go with Debian myself.

---

### Post by igknighted on 2007-03-22
On a computer that slow the initial setup would take forever to compile, but Gentoo well optimized with nothing extra installed might be the quickest.  As long as it's a box that you won't be messing with system stuff much then once you had it set up properly you wouldn't have to worry about the Gentoo'ness again.  From what I gather the slower the machine the greater the advantage compiling gives you.

EDIT: If you want to do some research and have a faster computer that could connect to the old one, I think there's a way to let the faster one help donate otherwise unused processor cycles to the slow one to cut down compile time during install/setup.

---

### Post by Big_Croc7 on 2007-03-22
Thanks for the suggestions!  I've looked around and found these as well: [http://delili.lens.hl-users.com/](http://delili.lens.hl-users.com/) and [http://vectorlinux.com/](http://vectorlinux.com/)
I'd thought about DSL and Puppy, but it looks like they take too much RAM (at least with a desktop; do they have a server-install type as well?)
As for Gentoo, I'm not sure I'm quite up to that stage yet ;-) but I might give it a try.
Looks like DeLi might even give me a desktop on it, though I don't really need that, but I wouldn't complain if I could get that too :-).

---

### Post by Big_Croc7 on 2007-03-23
Right, going to have a go this weekend then :-)
I'll try DeLi linux first I think, it would be interesting to see if I can get a functional graphical desktop with it, though it needs 350Mb for the full install; otherwise I'll try Debian, and if that dosen't work for some reason (or it's too slow) I'll have gentoo as my fallback.  Getting the disks now!

---

### Post by happy-and-lost on 2007-04-12
Stripped down DSL (!) is the way to go :)

---

### Post by Big_Croc7 on 2007-04-13
I thought DSL might take too much ram?

For now I've run into hardware problems though, so haven't had chance to try it out - possibly what happens when you leave a computer unused for too long.  Haven't figured out exactly what it is yet - seems to be something either bios/cmos or hard-disk related.

I'll definitely post if I get it working though!

---

### Post by CREEPING DEATH on 2007-05-02
> **Big_Croc7 said:**
>  It's a 486 with 8Mb RAM and a 180Mb HD; I was thinking of using a Debian absolute minimal install (from floppy disk) and getting just the absolute minimum packages for an Xserver.  Any comments?

You're kidding right?  That's barely enough for text-only, forget about any X server.  You have way too little RAM for anything else, and it'll take hours to install a text system.

CD

---

### Post by Big_Croc7 on 2007-05-10
Really? ah...

I haven't been able to try it yet due to hardware issuees, but assuming I get those fixed, any other suggestions then? would an old version of Debian work, if I can find a 10-year-old version anywhere?

All I need the system to do is connect to another machine, then login via xdmcp and use it as a terminal.  I guess my network card dosen't support pxe booting (plus that seems like a whole world of extra work!)  What's the absolute minimum I can use? DSL takes ~24Mb RAM, from what I've heard.

---

### Post by Cyvros on 2007-05-31
> **Big_Croc7 said:**
> Really? ah...

I haven't been able to try it yet due to hardware issuees, but assuming I get those fixed, any other suggestions then? would an old version of Debian work, if I can find a 10-year-old version anywhere?

All I need the system to do is connect to another machine, then login via xdmcp and use it as a terminal.  I guess my network card dosen't support pxe booting (plus that seems like a whole world of extra work!)  What's the absolute minimum I can use? DSL takes ~24Mb RAM, from what I've heard.

Sorry to revive an old thread, but...

DSL is small and very light-weight (it has a 50 meg size restriction, so one downside to it is that it doesn't use the latest version of the kernel - 2.4.x, I think), but if you really want something basic, you could look at a floppy-sized distro like [FDLinux](http://fdlinux.com/) or [muLinux](http://mulinux.sunsite.dk/) (as far as I can tell, both of these can run on as little as 8 megs of RAM). [Wikipedia has a good list](http://en.wikipedia.org/wiki/Mini_Linux#Floppy-distributions).

Hope it helps.

---

### Post by Big_Croc7 on 2007-06-05
Reviving a thread's fine :-)

Thanks for the links - I might give mulinux a try, don't think I'd heard of that one before.
DSL's too big I think though, and Fd linux looks like it's just designed to use an old PC as a router or similar.

---

### Post by Shazaam on 2007-06-08
Try this--
[http://www.toms.net/rb/](http://www.toms.net/rb/)

Runs off of 1 floppy :D

---

### Post by Big_Croc7 on 2007-06-09
That's a lot of stuff on one floppy :-D

thanks, might check it out... don't think it has an x server though, but it still looks cool.  cheers!

---

### Post by tukuyomi on 2007-06-09
> **CREEPING DEATH said:**
> You're kidding right?  That's barely enough for text-only, forget about any X server.  You have way too little RAM for anything else, and it'll take hours to install a text system.

CD
My experience can tell that Windows 95 can run very fine on it, with graphical installer, graphical bootsplash and graphical desktop, YES!:D. Could Linux be beaten on this field...? I'm searching too how to revive an old dusted PC, what about Slackware anyone?

---

### Post by Big_Croc7 on 2007-06-11
hmm... the thing is, I'm not sure as there's much that this computer could do on its own any more that would be terribly useful... but if I can use it as a terminal, it would make a quiet, cool and energy-efficient substitute for a second pc.  Getting a terminal running seems much easier with linux (at least, for me anyway :))

---

### Post by CREEPING DEATH on 2007-07-07
The [Debian Releases]("http://www.debian.org/releases/") page has links going back to 2.0 that would possibly work on a 486 with 8mb RAM.
Win95 will not work well on a 486 with 8mb, and Linux has come a loooonnnnnggggg was since 1992 or whenever the machine in question was made.  My 90Mhz PI has 24mb and is slow.
DSL is based on 3.0, 2.1 was current in 1999.
Expect a very long install time even using an obsolete version of Debian.  I know the text installer on 3.1 won't run on 8mb, I'd realisticly use 2.0 on a machine that old and try to find some RAM somewhere.
ETA:  I'm not sure the ISOs are still available, I can't find them on Debian's site any more.  More importantly, Synaptic certainly isn't on the older distro, Aptitude isn't on the older distro and I'm not sure apt-get is there either.  It may just be an exercise in futility.

CD

---

