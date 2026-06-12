---
title: "Can the latest kernel be packed to .deb ?"
date: 2006-07-17
forum: Desktop Environments
---

### Post by ss0007 on 2006-07-17
Hi ,
Everyone loves to be with latest kernel and to get the fast system .So , y cant someone post latest stable kernels into .deb pack and distribute and making it easy to install for newbies ? or even a script file like automatix ?

---

### Post by T700 on 2006-07-17
> **ss0007 said:**
> Hi ,
Everyone loves to be with latest kernel and to get the fast system .So , y cant someone post latest stable kernels into .deb pack and distribute and making it easy to install for newbies ? or even a script file like automatix ?

The latest, stable, kernals are available via the update system in Ubuntu. If you mean making the unstable, dev versions of kernals readily available for "newbies", in my opinion that would be a disaster.  There are people on this board that can't figure out how to burn an ISO or to to log in with sudo.  Do you really want an Automatix style program to get them a beta or alpha version of an OS?

Not a slam against those people, but to my mind, that's about the same as handing out handguns to preschoolers.  

Paul

---

### Post by ss0007 on 2006-07-17
hmm .. anyway .. thx for ur answer ,
if stable kernels are really available i've never seen an entry as kernel 2.6.17.x or so in synaptic entry!. Whr can i really find this and update my system , shld i add extra repos?

---

### Post by krazykirk on 2006-07-17
Thats weird... i can always easily find the kernels in synatic, just search 'kernel' in the search dialog, and scroll down down down till you get to linux-kernel something.

If it's not there you might need to enable extra repos? I'm not really sure.

Hope that helps! =)

---

### Post by ss0007 on 2006-07-18
thx again ,
i ll definetly look for it next time whn i boot to ubuntu ...

---

### Post by asplode on 2006-07-18
> **ss0007 said:**
> thx again ,
i ll definetly look for it next time whn i boot to ubuntu ...

Technically, the kernels *do* come in .deb files, from the repositories.

You are automagically downloading the latest, most stable, and well tested kernel with ubuntu-specific patches applied from aptitute (your package manager) whenever you update your system.  As someone above pointed out, there is no need for bleeding edge kernel packages, unless you feel like hacking on them yourself or testing them out, maybe trying to find a bug or see if the latest kernel release has hardware support for something currently unsupported by your current kernel.  Obviously those activities are for a specific audience, and furthermore, a source tarball makes much more sense for a bleeding edge release than does a .deb file, as not everyone who downloads or wants it would necessarily be running a debian based distro, and would much rather compile it for their specific platform anyhow.

---

### Post by iTrendsNET on 2006-07-18
I think he is talking about something like the newer 2.6.17 or 2.6.18 RC kernels.  In my experience, using a kernel that is not designed for the system (in the case of Ubuntu Dapper 2.6.15), can break things and cause you to have to do a lot of other upgrades that may result in an unstable system.  Add to that problems if you were, as an example, using the proper Dapper kernel with nvidia-glx added.  Wireless may or may not be a problem with a newer kernel that is not specifically taylored to work with your system.  

One thing I would like to point out is that Ubuntu seems to heavily patch their kernels.  Specifically, you may be running a 2.6.15 kernel, but Ubuntu has added in some of the best newer features of 2.6.16, etc.  So, again in my opinion, it is not really necessary to go through the trouble of going to a newer and non-standard kernel.  That is, unless you like to custom build your own.  :mrgreen:

---

### Post by linuxnewbie946 on 2006-07-18
There is a guide on how to compile your own kernel here [http://ubuntuforums.org/showthread.php?p=1270679](http://ubuntuforums.org/showthread.php?p=1270679)

---

### Post by glenn45 on 2006-07-18
Its good if the new kernel update is packaged as a .deb because, as in my case (and with maybe other people from the third world who does not have a reliable internet access), i couldn't update my ubuntu by simply clicking update. I have to do it by hand , meaning i have to download most of the .deb files. 
So right now im still using 2.6.17 and not 2.6.26 kernel.

---

