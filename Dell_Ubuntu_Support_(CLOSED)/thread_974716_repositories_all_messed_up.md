---
title: "repositories all messed up"
date: 2008-11-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by z987k on 2008-11-07
So got a new Dell Netbook and go to update it, possibly upgrade to 8.10 from 8.04 through apt and it turns out dell is shipping with broken urls, or someone changed them or something...

Orig sources.list
```
deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-backports universe main multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted

```

New sources.list that works for most stuff:
```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ports.ubuntu.com/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ports.ubuntu.com/ hardy universe
deb http://ports.ubuntu.com/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ports.ubuntu.com/ hardy multiverse
deb http://ports.ubuntu.com/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ports.ubuntu.com/ hardy-backports main restricted universe multiverse
# deb-src http://ports.ubuntu.com/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://ports.ubuntu.com/ hardy-security main restricted
deb http://ports.ubuntu.com/ hardy-security universe
deb http://ports.ubuntu.com/ hardy-security multiverse

```

Now I still get the error message:
```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.

```

what going on here?

---

### Post by cdtech on 2008-11-07
Check your System > Admin > Software sources and select from there. Be sure to uncheck the third party software sources that give you the probs.

Hope this helps ya.......

---

### Post by z987k on 2008-11-07
> **cdtech said:**
> Check your System > Admin > Software sources and select from there. Be sure to uncheck the third party software sources that give you the probs.

Hope this helps ya.......

No the default sources list all give 404s.

---

### Post by cdtech on 2008-11-07
There is no "binary-lpia" at that location:
[http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/)

---

### Post by z987k on 2008-11-07
> **cdtech said:**
> There is no "binary-lpia" at that location:
[http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/)

I noticed that to.  But why does the repository list shipped with the computer all give 404's?  Because it also doesn't exist.  wtf.

---

### Post by z987k on 2008-11-07
and further this whole lpia arch is just stupid. It's a massive hassle for every third part package out there, or anything not yet in the repos.  Everything is compiled for i386, I don't want to do the workaround posted for 30 some odd packages off the bat and then every time I need something not in the repos, which with lpia is a lot of things.

Do I need to just scrap the lpia version and re-install with i386? 
Seems the lpia isn't worthy of shipping with a system yet to be honest.

I mean I convinced my roomate to get the ubuntu version and singing it's praises, the thing gets here and I've been screwing with it for the past few hours just trying to install some basic packages.  I think he's ready to go back to windows... which is really sad.  In no way shape or form should this arch version be considered ready to go live, let alone for dell to ship it on a computer.

I mean if I wanted broken package managers with dependency hell etc, I'd got back to 2000 with an rpm distro.

---

### Post by linkunderscore on 2008-12-02
I am having the same issues. This reminds me of the first time I tried out linux back in 2000 (its funny that you mentioned that in your post :lol:). I gave up in a couple days after running into dependency hell....

..and now Ubuntu managed to allow me to relive that time in my life--which is cool, but wasn't really what i was going for when i installed UNR with the lpia kernel. 

What advantage does this give me over the i386 arch? Right now its just a huge pain in the ***.

---

### Post by armandh on 2008-12-02
I am dual booting vanilla 8.10 and dell 8.04 on the mini9
outside of one line of code to get the sound working in 8.10
[and that seems to fail if hibernated]
the i386 stuff seems to work including medibuntu which did not in the dell 8.04

---

### Post by jetpeach on 2009-01-03
i have a dell mini 12 and when i enable the default repos in synaptic, they give 404s. why is this again? i find it totally completely baffling because on my desktop it works, but the exact same line in the sources.conf gives 404 on the netbook! i don't get it!

ok, re-reading the thread, i see i have the lpia message too, so i guess this is because even though the packages for i386 are at those locations, i get a 404 because there isn't an lpia compiled package there? this does seem like a terribly confusing thing that new users would be frustrated with (afterall, just enabling the unchcked software repos in synaptic causes the errors, with little means to know why).

what is the benefit of lpia? speed? battery life? curious...

EDIT: some people have discussed this quite a bit
[http://ubuntuforums.org/showthread.php?t=993632&highlight=lpia](http://ubuntuforums.org/showthread.php?t=993632&highlight=lpia)
there consensus, "Dell Ubuntu +: faster bootup, all hardware "just works."
Dell Ubuntu -: slow wifi connect time (15-20 secs.), poky Dell launcher, limited to LPIA-specific software and 1 GB of RAM unless you want to fool with your system, no updates or patches of any kind in months."

also interesting,
[http://lwn.net/Articles/247003/](http://lwn.net/Articles/247003/)
lpia stands for "low-power on Intel architecture" (i didn't know this) and is similar to i386 but jacks the ability of the i386 packages to work...
[https://lists.ubuntu.com/archives/ubuntu-mobile/2008-January/001527.html](https://lists.ubuntu.com/archives/ubuntu-mobile/2008-January/001527.html)
this just shows they're trying to eliminate the "delta" between the lpia and i386 packages... i still don't see why the lpia packages aren't located at the same place as the i386 packages though

---

### Post by Talon2 on 2009-01-03
> **z987k said:**
> and further this whole lpia arch is just stupid. 


I have got to agree.

I've been using Ubuntu for nearly 3 years now and I had problems figuring out how to install apps like Realplayer 11 and Skype on my Mini 9.  This using .debs.

How on earth do the decision makers at Canonical expect non-technical users to come away with a positive experience?

---

### Post by anjilslaire on 2009-01-03
Indeed. I ran the Dell install for a few hours, long enough for me to leisurely back up my usb stick data in order to make it a bootable uab installer. I've loaded both Xubuntu 8.10 and Ubuntu 8.10, trying to decide which I prefer. But either way, it seems to far exceed the lpia distro. I can install anything I want, barring room on my 32gig SSD.

Go for it.

---

### Post by sirebral on 2009-01-03
I've been wondering the same thing about the LPIA since I noticed that XFCE is a smaller OS on the SSD then the LPIA OS is.  That was my WTF? moment.

I still have plans to just wipe the SSD dropping the Dellbuntu and going with Xubuntu. :KS It just seems logical to install an OS that requries 1.5GB on an SSD that holds 8GB, instead of placing an OS that requires 4GB there.  After the OS absorbs a certain amount for Swap and Page filing, you are pretty much left with 2GB if you went with the 8GB SSD.

I am not sure if you can blame DELL 100% for the LPIA thing though.  LPIA is an Intel research thing, and I find it odd they went with a full fledged Vanilla Ubuntu instead of trying to make LPIA work on XFCE, which would be obvious.  Intel really has it's hands as the crafter of LPIA.  Maybe DELL funded the research, but from all the complaints I am hearing so far it is a total waste of money and time.

---

### Post by anjilslaire on 2009-01-03
> 
After the OS absorbs a certain amount for Swap and Page filing, you are pretty much left with 2GB if you went with the 8GB SSD.


I've installed mine with no swap partion at all, to save read/write wear on the SSD. The only thing I've seen happen is hybernate no longer works, but suspend still woeks. This is on 512mb of ram, too.

Just some food for thought.

---

### Post by jetpeach on 2009-01-04
in Dell's defense (and although i probably won't use the LPIA install in the long term) i *do* like the idea of compiler optimizations. If there was a program that made installing i386 programs and .debs on the LPIA easy (there are workarounds right now, but all appear tedious), and if the standard repos had all the programs recompiled with LPIA, then i would actually be in favor of it - extended battery life, better performance, and just through compiler optimizations? sounds good to me.

however, in its current form, it is more problematic than good. i appreciate Dell's effort though and will still buy there pre-installed Ubuntu hardware.

---

### Post by sirebral on 2009-01-04
> **jetpeach said:**
> in Dell's defense

You mean Intel's defense.  Intel is the company researching and making the LPIA.  It means Low Power on Intel Architecture and it is their research project.

I think the LPIA material is premature.  Even if the research is ready for it to be released it isn't ready to be released into the mainstream market because it is not easy to adopt.  The adoption would be DELL's and Canonical's shame.

---

