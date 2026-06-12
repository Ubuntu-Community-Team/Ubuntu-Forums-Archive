---
title: "[SOLVED] Optiplex Frustration"
date: 2007-08-05
forum: Dell  Ubuntu Support
---

### Post by Nolroz on 2007-08-05
Allright guys, first off thanks to everyone for posting on this topic.  I am at my wits end and would be even worse off without all of your input on the matter.

I have been trying for over a week now to get my Optiplex 320 switched over to Linux. I started with Ubuntu Studio dual booted with XP and had no love with the linux. I gave up on the dual boot a while ago fearing that I might have installed two different boot loaders and might just be making things worse.

I have tried everything that I can find on the topic from attempting to use Lilo and Grub2 to a bunch of different Linux distros and even hauling my computer to a friends house to see if I had a problem with my internet settings or something.

Apt-get and aptitude install both return that they dont know about anything called lilo, or grub 2.

I can get Synaptic to install lilo for me, but I dont know if this is diffrent from chrooting and installing from command line, or if it does the same thing.

After installing lilo I usually can't get liloconfig to run (it did once, but dissapeared when I went to go modify my fstab)

I have also tried downloading the packages and putting them on a flash drive but cant seem to get the packages to work. Grub 2 tells me that it needs Libpc (not sure if thats correct) as a dependency, which I cant find or cant get to work.

If anyone knows why I cant get lilo or grub to install from apt-get or aptitude, that would be sweet. I use wireless on all my computers, could my router settings or something be the reason why I cant see any packages? 

Do I need to do something like chrooting before attempting to install from the flash drive?

And where in the alternate install CD does it let you chose lilo over grub. It just blows past and installs grub every time for me!

Anyways, thanks again everyone. Any help would be awesome.

---

### Post by Nolroz on 2007-08-06
Ok, well I finally got it to work.:guitar:

For those of you out there who are banging your heads against the optiplex, get the alternate install cd, start the process and at some point before you get too far, go back a step.  from there it lets you chose what you want to do from a list, choose install lilo, and it is WAY easyer than dealing with the command line action (plus I never got it to install lilo properly):)

---

