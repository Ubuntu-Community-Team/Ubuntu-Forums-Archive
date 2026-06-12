---
title: "Scibuntu"
date: 2006-11-08
forum: Education &amp; Science
---

### Post by Bionic_Beefpile on 2006-11-08
I saw this script posted over on Digg today:
[http://urban.it.hik.se/scibuntu/](http://urban.it.hik.se/scibuntu/)

It's sort of an "automatix" for science-related programs.  I came here to do a quick search and learn more about it, but I didn't pull up any posts in the forums.

Does anyone use this?  Anyone interested in setting up a wiki for documentation of the included programs?

---

### Post by glotz on 2006-11-08
Looks like fun. Uhm, why don't you edit the wiki?

---

### Post by Bionic_Beefpile on 2006-11-08
Hehe my level of knowledge on these programs is less than complete.
I ran the script and it installed a few things, but I've got some problems.  Several of the programs just crash whenever I try to run them (under Edgy).  Also, my acroread plugin for Firefox seems to be broken.

---

### Post by Bionic_Beefpile on 2006-11-08
Actually I think this managed to break Beryl pretty severely as well.  I had to use a failsafe terminal to remove beryl-manager because anything else I tried led to an X crash.

::EDIT:: right, this script tries to install libgl1-mesa-swrast which dumps to libgl1-mesa-swx11 which uninstalls libgl1-mesa-dri and libgl1-mesa-glx, as well as all of the beryl components.  I'd recommend staying away and just installing the individual software packages manually, I guess.

---

### Post by LaserJock on 2006-11-08
I'd really, really like to encourage people wanting to do things like Scibuntu to contact the Ubuntu science development team for Universe (MOTU Science). PM me if you want more info. We will most likely be working on official ways to easily install science package groups for Fesity. The Scibuntu script does a couple of odd things like use -q with apt-get so they don't see that there is a typo for treeviewx and installing acroread from Adobe rather then the Ubuntu repositories. 

In general, creating a script to install packages is handy for personal use, but not so great at all for widespread distribution. We should avoid duplicating effort and doing things through the development community has the added benefit of making things available to all Ubuntu users. There are already a ton of Ubuntu derivatives, maybe we shouldn't be confusing users by creating a whole new name for an apt-get script.

-LaserJock

---

### Post by AlphaMack on 2006-11-11
I would recommend hand-editing the script, especially if you're on a PowerPC.  Not only does it break 3D acceleration without an explanation as to why it needs libgl1-mesa-swrast, but it installs the i386 release of Reader, which is useless on a PPC box.

---

### Post by urban_a on 2006-11-12
There are two new releases of Scibuntu to try out!  scibuntu022-alpha which is a bugfix release and scibuntu03-testing which includes more programs and more functionality. [http://urban.it.hik.se/scibuntu/](http://urban.it.hik.se/scibuntu/)

Please report bugs to me! Both scripts are in alpha stage although scibuntu03-testing is more alpha than 0.22. But if the programs get installed but don't run, don't blame me an apt-get is an apt-get even if it's included in a script. Then search for the problem lower down in the food-chain. 

And yes, this was meant for personal use first, but it seems to fill out an empty ecological niche.   

Urban

---

### Post by Zdravko on 2006-11-14
I proposed Scibuntu as an additional flavor for the next release. Discussions go here:
[http://ubuntuforums.org/showthread.php?t=298784](http://ubuntuforums.org/showthread.php?t=298784)

---

