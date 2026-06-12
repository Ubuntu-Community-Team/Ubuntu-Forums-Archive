---
title: "New Kernel Updates"
date: 2006-01-30
forum: Desktop Environments
---

### Post by Bukunut on 2006-01-30
Hello All

How often do updates to the kernel get posted to the repositories? At the monent I am running 2.6.12-10-686, I see 2.6.14 has been available sometime, and whilst newer versions are available I see problems have occured to users who compiled their system with the new one.. 

Bukunut

---

### Post by Sutekh on 2006-01-30
As far as my knowledge goes, newer kernels become available through Ubuntu's repositories once they are 'tailored' (for lack of a better word) to Ubuntu.  

You can compile your own newer kernel (2.6.14, 2.6.15.1, etc) if you like, but I'd rather leave the kernel compilation to the Ubuntu devs and wait for releases.  I'm sure the majority of users will be fine using slightly older versions of the kernel.

---

### Post by Bukunut on 2006-01-30
Sutekh

Thanks for the reply, I wondered about updates to the kernel. I like you would rather wait for the updates, just as seeing the number of new releases I wondered how often they do get released to the repositories. 
Thank you - Bukunut

---

### Post by towsonu2003 on 2006-01-30
[QUOTE=Bukunut]Hello All

How often do updates to the kernel get posted to the repositories? At the monent I am running 2.6.12-10-686, I see 2.6.14 has been available sometime, and whilst newer versions are available I see problems have occured to users who compiled their system with the new one.. 

Bukunut[/QUOTE]
hi,
breezy won't get an update for the kernel unless there is a security issue with the existing kernel. that's basically a general policy that applies to everything, which is why we do not get firefox 1.5 from the repos. 
if you need a new feature (a driver? something else?), you'll need to compile it yourself. there was a howto in the tricks section on how to compile a kernel. from my point of view, it is a long and complicated thing to do unless the feature you need is critical.

PS. I believe the new ubuntu (6.40, dapper) will have the latest kernel at time of release.

---

### Post by Sutekh on 2006-01-30
[QUOTE=Bukunut]Sutekh

Thanks for the reply, I wondered about updates to the kernel. I like you would rather wait for the updates, just as seeing the number of new releases I wondered how often they do get released to the repositories. 
Thank you - Bukunut[/QUOTE]

I'm really not too sure.  I been using Breezy since it's release.  I memory serves, I'm pretty sure there has only been one change; 
2.6.12-9 -> 2.6.12-10

---

### Post by Bukunut on 2006-01-30
Thanks guys! I appreciate your answers.

Bukunut

---

### Post by Eversmann on 2006-02-04
Does anyone have already installed a kernel compiled on his own on Breezy? Actually i need kernel 2.6.14 (at least) to make my pcmcia work. I've tested Kanotix with that kernel and saw it that way.

Actually, with 2.6.12-10 i get that "DANGER blah blah blah remove power from the socket" and couldn't solve it with all the tricks found on google and this forum.

Anyway, i can always compile one kernel and add it to the grub screen and see how is goes, isn't it?

---

### Post by Brando569 on 2006-02-05
[QUOTE=towsonu2003]there was a howto in the tricks section on how to compile a kernel. from my point of view, it is a long and complicated thing to do unless the feature you need is critical.[/quote]

actually its not really that hard, within my first month of using ubuntu i compiled my first kernel, using the "kernel compilation for newbies" guide. use that or even the howto for 2.6.14 vanilla with the patches its actually really simple. just follow the guide. all you pretty much do is d/l dependancies, kernel source, and patch, extract the source, soft link the directory, compile the configuration tool, select a few things, close outta that and do the regular steps that you would use to compile any other program (except for ./configure)

> PS. I believe the new ubuntu (6.40, dapper) will have the latest kernel at time of release.

most likely it will be outdated within a month or two... but most ppl can live with that

---

### Post by Velvet Elvis on 2006-02-05
FWIW, Slackware uses an unpatched kernel.org kernel by default, making it one of the easiest distros to use with a handrolled kernel.   Ubuntu has an ungodly number of patches added to the kernel which makes it better in most cases but a real PITA if you need to roll your own.  If you've never configured and complied a linux kernel before, Ubuntu is not the distro to use in learning.

---

### Post by missmoondog on 2006-08-28
> **Sutekh said:**
> I'm really not too sure.  I been using Breezy since it's release.  I memory serves, I'm pretty sure there has only been one change; 
2.6.12-9 -> 2.6.12-10

i realize this is an older thread, but we're talking breezy here anyway. 

that is the only linux kernel update to breezy, as i just installed breezy on an old computer yesterday (8/27/06). came looking to see why it is using that old of one. of the updates to the kernel since breezy, none have been of a security nature to warrant posting to the breezy repository's?

i'm not even about to go through all those hoops of rolling my own, no matter how good/simple the how to is. ](*,) 

if there is a security issue with this old kernel, it would still get posted to the repos, correct?

thanks

---

### Post by jdong on 2006-08-28
Breezy is still a supported Ubuntu release, and if something of a security nature affected Breezy's kernel, it'd be updated by the Ubuntu Security Team.


Generally, older kernels are more time-tested and have already had their security vulnerabilities exposed.

---

### Post by missmoondog on 2006-08-28
cool. that eases the mind, i guess. ;)

thanks

---

