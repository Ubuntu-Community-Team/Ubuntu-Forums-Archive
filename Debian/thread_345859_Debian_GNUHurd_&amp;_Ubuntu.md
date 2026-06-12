---
title: "Debian GNU/Hurd &amp; Ubuntu?"
date: 2007-01-24
forum: Debian
---

### Post by handy on 2007-01-24
After following a looong running thread in this section of the forum about Debian & Ubuntu, it caused me to wonder about Ubuntu's future?

Debian are working on GNU/Hurd, & from what I understand, ***GNU***/Hurd would suit the Debian philosophy more than the Linux kernel, or more precisely Linus Torvalds' licensing philosophy does.

It makes me wonder if in 7 years (a picked out of the sky number) we might find that Debian is/has dropped support for the Linux kernel & is all about the GNU/Hurd?

If so that would mean that the Debian repositories would eventually be converted to the GNU/Hurd kernel & Ubuntu being basically an easy to use desktop Debian would be using that kernel too...

I know little about these matters, they do intrigue me though, hopefully they stimulate some conversation so that I can learn more about the topic, your thoughts will be greatly appreciated?  :) 

Some links for anyone interested:

_***[http://www.gnu.org/software/hurd/hurd.html#introduction](http://www.gnu.org/software/hurd/hurd.html#introduction)***_

*_**[http://www.debian.org/ports/hurd/](http://www.debian.org/ports/hurd/)**_*

---

### Post by julian67 on 2007-01-28
It's difficult to see debian ever dropping support for linux as long as the linux kernel is acceptably licensed (it is and it will continue to be, it's out in the open and there's no going back) and functional.  Hurd development has been extremely slow. I heard RMS on a podcast recently saying that the technical obstacles with developing Hurd have proven far greater than ever anticipated. He didn't give a roadmap/timescale for a version 1.0 and didn't sound too optimistic either, though of course that's only my impression. 

There would have to be some unforseeable calamity with the linux kernel to get a lot of effective people to switch to developing Hurd. Right now people are going to be putting their effort in where they know it will count in useable and used environments. 

In terms of freedom the Hurd kernel would seem ideal, 100% free with no proprietary blobs of unknown source, but the momentum is definitely with the Linux kernel. 

Personally I think in the very long term the Free Software Foundation and GNU project is far more important than the Linux kernel or BSD and derivatives, or any other kernel,  because the benefit of using GNU/Linux in preference to proprietary software is derived more from the  freedom than technical accomplishment (though that is mostly superior too), but right now it's the Linux and BSD  kernels that make that freedom available to us, the users.

---

### Post by xabbott on 2007-01-29
Hurd will be in a perpetual state of development. The last time I heard RMS talk about it he said GNU was more concerned with Gnash and didn't see Hurd as a priority. I also think he mentioned how the original design in execution didn't end up as good as they planned.

---

### Post by maxamillion on 2007-01-29
I don't think debian GNU/Linux will ever be dropped, if in the event HURD takes the main stage, I could see Linux taking a back seat to it just like the other ports of debian have to Linux as of now..... 

I also don't see HURD jumping up and taking over any time soon, Linux currently has over 10 years of development and support to have gotten it to where it is now (and we all agree that there is still room for improvement).... but that's just my opinion.

---

### Post by az on 2007-01-29
If the Hurd was to become more popular, it would not take long before there was an Ubuntu port of it.  That would happen long before Debian would ever consider dropping support for x86 architecture.

For Debian to switch from one kernel to another would not happen overnight.  Consider a software patent nightmare where you basically would need to rewrite the entire kernel.  If it would make more sense to just port to a different kernel, then that's what would happen.  I can imagine there would be some sort of migration path.

Packages are uploaded as source and (with the exception of kernel modules) are usually kernel-agnostic.  Since the Hurd filesystem is ext2/ext3, it would be possible (I imagine) to boot into a HURD, BSD or other Unix-type kernel and dist-upgrade every single package on your box to the new kernel compatible binary.

Anyway, it won't happen and even if it does, it would only be fascinating.

---

### Post by deanlinkous on 2007-01-29
I see solaris kernel being GPL and providing us a kernel choice before the HURD works well enough to be useful.

But I do hope the HURD develops into something.....

Heck we already have Nexenta - open Solaris/Ubuntu! So once openSolaris goes GPL we will have something to build off of already. 

RMS is just fine with linux - it is free software afterall....

---

### Post by mips on 2007-01-29
> **deanlinkous said:**
> I see solaris kernel being GPL and providing us a kernel choice before the HURD works well enough to be useful.


I just want their file system, **[ZFS]("http://www.sun.com/2004-0914/feature/")**

---

### Post by handy on 2007-01-30
So, what about Debian & BSD?

Is there a future Ubuntu on BSD?

BSD does seem to be picking up momentum.

---

### Post by deanlinkous on 2007-01-30
[http://www.debian.org/ports/kfreebsd-gnu/](http://www.debian.org/ports/kfreebsd-gnu/)
[http://www.debian.org/ports/netbsd/](http://www.debian.org/ports/netbsd/)

---

### Post by handy on 2007-01-31
Quite possibly, but who knows looks like the answer... :KS

---

### Post by xabbott on 2007-02-01
> **handy said:**
> So, what about Debian & BSD?

Is there a future Ubuntu on BSD?


Even if Debian creates a distribution using BSD I don't think Ubuntu needs to follow. One of Debian's strengths is it's versatility. Ubuntu's strength has been taking a very large and versatile project and focusing it on one specific area, desktop.

> **handy said:**
> 
BSD does seem to be picking up momentum.

I assume you mean for desktops? I'm just confused by that...so I'll wait to comment until clarification.

---

### Post by handy on 2007-02-02
> **xabbott said:**
> Even if Debian creates a distribution using BSD I don't think Ubuntu needs to follow. One of Debian's strengths is it's versatility. Ubuntu's strength has been taking a very large and versatile project and focusing it on one specific area, desktop.



I assume you mean for desktops? I'm just confused by that...so I'll wait to comment until clarification.

Yes, for desktop is what I meant... :D

---

