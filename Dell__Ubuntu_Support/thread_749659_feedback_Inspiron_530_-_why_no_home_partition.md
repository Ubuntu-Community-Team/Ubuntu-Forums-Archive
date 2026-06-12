---
title: "feedback Inspiron 530 - why no home partition?"
date: 2008-04-08
forum: Dell  Ubuntu Support
---

### Post by davidpbrown on 2008-04-08
I don't know if Dell reps are lurking but just to suggest that I'm *very* happy with the Ubuntu Inspiron 530. Worth every penny.

The only surprise I had was that it came all lumped as one partition (aside from an apparently redundant Dell Media partition and a swap)

It seems rather odd that there isn't at least a separate /home partition, as I see this is one of the substantial strengths of Ubuntu.. saving setting on upgrades and reinstallations.

Wiping the Dell Media and reinstalling with new partitions was slightly sticky as gparted struggled to remove the first partition (maybe because it was trying to be HPA?) but anyhow formating it as ext2 beforehand made it work easily enough.

I've been missing sound for a year now waiting for Creative drivers etc.
It's a big plus to have hardware that just works..

Thanks! :)

---

### Post by wyth on 2008-04-13
I have a 530 as well, bought with Ubuntu 7.10, and am as happy with that as I have been with any computer I've ever owned.  Maybe moreso.  

As far as the /home partition question goes, any typical install would always include /home as part of the main partition, and not put it on its own partition.  There are a number of guides out there about moving /home to its own partition, but it's something one generally has to tell a typical installation to do, rather than have that done out of the box.

But I agree, it would be a better set-up.  I think the only thing standing in the way of something like that is it might introduce some needless complication to newer users (Whadaya mean my My Documents folder is on another hard drive?).  But you're clearly a savvy enough user to pop in a live cd or get gparted on a live cd, make the partition, and do the necessary fstab readjustments.  It was a snap on my 530.

---

### Post by kerry_s on 2008-04-13
it's safer, 
1. you don't run out of space being locked into the size of the partion created. 
2. it's not always safer to keep old settings when up grading to newer programs, they may use different settings.

i don't use a separate /home partion for my install and i do mine custom.

---

### Post by wyth on 2008-04-14
> **kerry_s said:**
> 
1. you don't run out of space being locked into the size of the partion created. 
2. it's not always safer to keep old settings when up grading to newer programs, they may use different settings.

kerry_s, do you reconfigure all your settings on every upgrade, then?  

As far as partition size/space, drive space is not really at any sort of premium, and with tools like gparted (available via a live cd for maximum utility), it's easy and safe enough to increase and decrease partition space.  (I just did this with a partition I have set aside for multimedia.) Have you run into issues with running out of space?

Just curious.

---

### Post by davidpbrown on 2008-04-14
I was wondering the same.. with drives now measured in fractions of terabytes.. give the system 30GB and I can't imagine it being a problem for anyone who can't then make it what they need.

---

### Post by apswartz on 2008-04-14
I have been using Linux since 1999 and I have always had a separate /home partition. To not have one seems shortsighted. It makes upgrade much easier!

---

### Post by davidpbrown on 2008-04-16
So here's an unfortunate case in point..

I tried yesterday to update to Hardy, having had no problems on the laptop.

Upgrade to Hardy crashed badly.. couldn't even get a command line and the previous kernel version appeared so confused it couldn't function as a fallback.

Hardy's still in beta for ~8 days but still this was a surprise. I hope this doesn't affect everyone on a Dell Inspiron as I wonder that the package manager will encourage distro upgrades??

The error appears to be kernel not finding sata drives.
ata1.00 revalidation failed(errno=-5)

Bug is reported here.. 
[https://bugs.launchpad.net/ubuntu/+bug/217926]("https://bugs.launchpad.net/ubuntu/+bug/217926")

So, I just reinstalled from CD back to Gutsy and having a /home partition (and some /etc backups) this was really painless, if a little time consuming.

---

### Post by wyth on 2008-04-16
I had this same problem a couple weeks ago.  I could never work out whether it was the SATA issue or something to do with my Nvidia 8600GT card.

I reinstalled 7.10 as well (and was very happy I had a separate /home partition -- made the reinstall painless and fast).

We know that the 7.10  that came with the 530n setup was configured to work with the hardware by Dell.  We also know that Dell will of course be supporting an LTS distro.  

However, it may be a little while before the support is fully online -- they may have to wait until the updates are done, and then work in any necessary patches, etc. 

I've checked the Dell Linux wiki and forums for any info, but the wiki is blank on this, and their forums are... they're not like this.  Not that they're bad or anything, but the questions and problems are generally more basic, and I didn't see anyone asking about updating to the new beta version of an LTS distro.  

If nothing else, the Dell Linux support line is 1-866-622-1947.  If no one has any answers about Hardy on the Del equipment soon, it might be worth an email or a phone call.

---

### Post by davidpbrown on 2008-04-17
Thanks - yes..

I'm not sure if you're suggesting the 7.10 Dell disk is actually different that a standard Live disk.. I'd taken it to be the same. Interesting if not.

I'd found some references to that error from previous distributions, so I expect it will affect a few people and then be recognised and corrected in time.

If I remember, I'll post again if/when I see this obviously corrected.

---

### Post by notwen on 2008-04-17
> **davidpbrown said:**
> Thanks - yes..

I'm not sure if you're suggesting the 7.10 Dell disk is actually different that a standard Live disk.. I'd taken it to be the same. Interesting if not.

I'd found some references to that error from previous distributions, so I expect it will affect a few people and then be recognised and corrected in time.

If I remember, I'll post again if/when I see this obviously corrected.

Dell releases their own custom Ubuntu images w/ specific drivers for specific models they offer Ubuntu on.  Check [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO") for more info.  They normally get these out a month or two after the official Ubuntu release.

---

### Post by basotl on 2008-04-17
Well the when you perform a Guided installation with the live CD it also does not create a separate /home partition.

Before using Ubuntu I had been used to having a /, swap, /home, /var, /usr and any other partitions I felt necessary. Now I just use / without even having a swap (plenty of ram no need). I tried using a /home partition but I found it space restrictive and have stuck to the one-partition-to-rule-them-all that Ubuntu seems to like.

I also just upgraded from Gutsy to Hardy yesterday. No problems experienced on my laptop. It's an Inspiron 9300 laptop.

---

### Post by wyth on 2008-04-18
> **notwen said:**
> Dell releases their own custom Ubuntu images w/ specific drivers for specific models they offer Ubuntu on.  Check [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10#Dell_OS_Reinstallation_7.10_DVD_ISO") for more info.  They normally get these out a month or two after the official Ubuntu release.

That's what I was talking about.  Although when I reinstalled 7.10, I just used the live cd that came with the setup, and I don't believe that was any specialized image (but I'm not sure).

---

