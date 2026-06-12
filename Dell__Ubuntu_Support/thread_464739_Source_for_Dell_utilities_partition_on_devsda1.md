---
title: "Source for Dell utilities partition on /dev/sda1"
date: 2007-06-05
forum: Dell  Ubuntu Support
---

### Post by benanzo on 2007-06-05
Anyone know if the source for the Dell DOS utilities on /dev/sda1 (on the preinstalled systems) is available?  I didn't see any licensing information so I was wondering if it was Free or something Dell wants to keep secret.  I want to evaluate the possibility of porting them into the Linux environment or moving them off to a CD.

---

### Post by pyros on 2007-06-05
> **benanzo said:**
> Anyone know if the source for the Dell DOS utilities on /dev/sda1 (on the preinstalled systems) is available?  I didn't see any licensing information so I was wondering if it was Free or something Dell wants to keep secret.  I want to evaluate the possibility of porting them into the Linux environment or moving them off to a CD.

If I am not mistaken, the utilities are most definatly closed source, the liscense agreement for the packages there are the same as the liscense agreement for the computer itself and can be found on the back of your invoice or packing slip.
However, they don't really need porting, as they run independant of the operating system. On newer systems, I belive you can launch them from a bios boot menu. There should also be a copy of the same utilites on your system resource cd, which can be used by booting off of said resource cd.

---

### Post by benanzo on 2007-06-05
I understand they don't need porting, but I am really looking for a way to get them off the drive without just deleting them.  I either want to move them into my Linux environment or onto a bootable CD.  The new Dell systems that shipped with Ubuntu (which is what I have) don't come with a resource CD other than the standard Feisty install disk.  This offers little room for those of us who want to reorder that partition scheme to do so.

Ideally I would like to port those utils into Linux so I don't have to worry about keeping that DOS partition on my disk, or at least moving them off to a boot cd.

---

### Post by magicfab on 2007-06-05
> **benanzo said:**
> Anyone know if the source for the Dell DOS utilities on /dev/sda1 (on the preinstalled systems) is available?  I didn't see any licensing information so I was wondering if it was Free or something Dell wants to keep secret.  I want to evaluate the possibility of porting them into the Linux environment or moving them off to a CD.

That's a good idea.

I am 100% positive the licence on those utilities is not free. The BIOS code itself is not free so in terms of freedom, that's a tradeoff you have to live with if you want to use those utilities. It seldom happens, but it's useful to keep that around on a CD as you say. I think this would only fit on a DVD judging by the size of the partition itself (2GB) although I could be wrong.

The first step to doing that I guess would be to use something like FreeDOS (is that what load when you enter that partiition ?) and look for partition imagers that would ket you copy the entire portition and start playing wth that on a DVD.

If you do such a thing I'd be happy to review your work on my own (free) time.

Cheers,

---

### Post by nescafe1001 on 2007-06-05
> **benanzo said:**
> Ideally I would like to port those utils into Linux so I don't have to worry about keeping that DOS partition on my disk, or at least moving them off to a boot cd.
Well, porting the diags to a Linux environment is probably not possible, because the diags require raw hardware access to do their thing, and the access they require would confuse the kernel to no end.

However, you should be able to copy the diags to any bootable DOS media and still be able to run them.  A cheap 64 meg memory key with FreeDOS installed would probably work fine.

Or you could just leave the diags in place -- the partition itself is only 48 megs, so you are not losing much space and it will make the lives of the Dell support reps easier if they need to run diags at some point in the future. :)

---

### Post by EndPerform on 2007-06-05
Hmm, so it's a standard Feisty CD.  Try checking the Dell support site and see if they offer the system diagnostics as a download.  I believe they do, but it's been a while since I've had to go out to their support site.

---

### Post by pyros on 2007-06-05
> **EndPerform said:**
> Hmm, so it's a standard Feisty CD.  Try checking the Dell support site and see if they offer the system diagnostics as a download.  I believe they do, but it's been a while since I've had to go out to their support site.

Indeed they are, can't belive I forgot that,,,

---

### Post by fjgaude on 2007-06-05
Say, what's the URL of this Support Site where the diags are? Thanks!

frank

---

### Post by pyros on 2007-06-05
[http://support.dell.com](http://support.dell.com)

---

