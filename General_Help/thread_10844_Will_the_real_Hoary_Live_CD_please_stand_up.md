---
title: "Will the real Hoary Live CD please stand up?"
date: 2005-01-11
forum: General Help
---

### Post by stoneguy on 2005-01-11
On one hand, in [http://lists.ubuntu.com/archives/ubuntu-devel/2005-January/003044.html](http://lists.ubuntu.com/archives/ubuntu-devel/2005-January/003044.html), 
we have its announcement from Matt Zimmerman. On the other hand, from [http://www.gnoppix.org](http://www.gnoppix.org), we have the announcement of GNOPPIX Developer version 0.9.2b5 Hoary.

Just what is the relationship? Is the Matt-version superceded? I don't mind - it hasn't worked too well here.

---

### Post by misGnomer on 2005-01-13
Both the recent MDZ's alpha and Gnoppix beta releases of "Hoary live CD" have appeared to be normal install versions (i.e. not booting into live CD mode).

The only one that has worked was the Morphix 0.5-pre4 release which uses GTK and Xfce instead of Gnome. That was surprisingly sweet and light-weight, but it's no Hoary. It'd be actually interesting if this Morphix "Light-GUI" would turn into a "mini-Ubuntu live CD" for the low-end systems.

I've also wondered about the relationships between the Ubuntu devs, Gnoppix devs and Alextreme of Morphix. Although they're all supposed to cooperate, there seems to be no outward coordination and all appear to pursue their past live CD projects in their own old quarters. Perhaps they simply have some commonly adopted guidelines and the occasional email exchange but it is not easy to see where the synergy lies. Ideally there would be a single Gnome live CD forum where all knowledge and enthusiasm is concentrated.

It's also a little unfortunate that none of these developers seem to frequent this forum, even to announce new (alpha/beta) releases of the live CD or explain what they're made of. Although it's been mentioned that the Gnome live CD's are increasingly diverging from the Knoppix mould, I've only ever seen a comprehensive list of boot parameters for Knoppix.

What comes to the "real Hoary live CD", I'd expect such a beast to eventually surface somewhere in the various Ubuntu download directories but the life here in the Ubuntu live CD forums will go on as before...

---

### Post by daniels on 2005-01-13
We are working with Gnoppix -- the latest releases are the result of a joint effort by Matt Zimmerman (Ubuntu) and Andreas Mueller (Gnoppix), among others.  The reason they don't fully boot into live CD mode (no X) is because they are incomplete; I uploaded X with the changes necessary to reconfigure on the fly (generic tip: sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/xfree86/xorg.conf.md5sum' && XORG_FORCE_PROBE=yes sudo dpkg-reconfigure -phigh xserver-xorg, to force reconfiguration and reprobing of yoru configuration, if you have xserver-xorg >= 6.8.1-1ubuntu10) a couple of hours ago, so live CD builds starting from the day after tomorrow should be working fine.

The reason there's been so much change is that we now use a fully installed Ubuntu system, rather than a Knoppix derivative which was actually nothing like Ubuntu.

---

### Post by stoneguy on 2005-01-13
Thanks Daniel.

What I was looking for was a downloadable Hoary Live ISO, feature complete to Xorg, that I could test on a few different systems and provide feedback. Sounds like I'm a bit premature.

Where should I be looking for such an ISO, at Ubuntu or Gnoppix sites? I knew you guys were working together. Wonderful idea; I'd like to see more of that kind of activity, in place of the current mushrooming of distros with the lifespan of mayflies. But I haven't seen anything about division of roles/responsibilities. To add my 2 cents to misGnomer's, a joint statement on both sites would clarify.

---

### Post by amu on 2005-01-13
[QUOTE=stoneguy]Thanks Daniel.

What I was looking for was a downloadable Hoary Live ISO, feature complete to Xorg, that I could test on a few different systems and provide feedback. Sounds like I'm a bit premature.

Where should I be looking for such an ISO, at Ubuntu or Gnoppix sites? I knew you guys were working together. Wonderful idea; I'd like to see more of that kind of activity, in place of the current mushrooming of distros with the lifespan of mayflies. But I haven't seen anything about division of roles/responsibilities. To add my 2 cents to misGnomer's, a joint statement on both sites would clarify.[/QUOTE]

downloading? you may decide this yourself. Gnoppix is still Gnoppix.I'm working still on the next generation liveCD. I test every snaphot CD, amd64 powerpc and i386, if there's  a ( alpha,beta)  version, which just works ( better than the other before) I put them to the Gnoppix Servers. If the development is finished, Gnoppix get back his typical brand. Best best way reporting about your livesession is on the u-devel maillinglist. Reporting problems, feel free to use the BTS.

Thanks,
amu

---

### Post by amu on 2005-01-13
[QUOTE=misGnomer]
It's also a little unfortunate that none of these developers seem to frequent this forum, even to announce new (alpha/beta) releases of the live CD or explain what they're made of. Although it's been mentioned that the Gnome live CD's are increasingly diverging from the Knoppix mould, I've only ever seen a comprehensive list of boot parameters for Knoppix.

[/QUOTE]

Sorry for it, but atm, the current stage is development, the livecd concept is completely revised. The prevered way of communication is still email.

Cheers,
amu

---

### Post by daniels on 2005-01-13
[QUOTE=misGnomer]It's also a little unfortunate that none of these developers seem to frequent this forum, even to announce new (alpha/beta) releases of the live CD or explain what they're made of. Although it's been mentioned that the Gnome live CD's are increasingly diverging from the Knoppix mould, I've only ever seen a comprehensive list of boot parameters for Knoppix.[/QUOTE]Most of the developers (including, it must be said, myself) vastly prefer email as a method of communication, and mailing lists for widespread discussions.

---

### Post by misGnomer on 2005-01-14
Daniel & amu,

It would be much appreciated if you developers simply posted some messages about the status of development and other tidbits and links to test releases. Currently anyone interested in the Gnome live CD scene must try and scrape together meager info far and wide without still getting very far.

For instance, you could start a simple blog and leave a note of its address here. We'd then have something more to chat about on this live CD forum.

It would also be great if the live CD's included a prominent and easy-to-use tool for submitting information back to you about bugs, hardware incompatibilities etc. Something that collects hardware details (and relevant config data) automatically and also allows saving the data e.g. on a floppy (if network doesn't work) for later transmission from a functional Linux system. Heck, perhaps you'd even like to know when stuff works perfectly as that could help troubleshoot obscure problems. Of course, it would be coolest of all if OSDL or some other neutral Linux organization then maintained a master database of such data so that the effort could be shared across distros for everyone's benefit. With some XML pixie dust, Ubuntu could datamine data that only applies to specific Ubuntu version, or cast the search net wider and learn how specific hardware/software combinations act on other distros.

Live CDs would be ideal for new Linux converts or just folks trying out new hardware to both test-run Linux and check their hardware compatibility at the same time while providing useful feedback data back to to the central database. Of course, since the kernel development is fast and furious, it'd be useful to have more frequent unofficial test-liveCDs with the latest kernels to test...

Sorry for getting off topic, but I feel that the live CDs are really the greatest if underutilized resource for catching people's imagination while effectively taking advantage of the potential for useful feedback.

---

### Post by daniels on 2005-01-15
We're working on a hardware database, but unfortunately, we're basically at the situation where lots of things are in flux, and we're spending every waking hour fixing stuff instead.  The blog would be rather uninteresting -- X used to be broken one way so it wouldn't configure properly (my fault), and today X is broken in another way so it won't configure properly (Perl's fault).  We try to make announcements and the like when interesting stuff happens.

---

### Post by misGnomer on 2005-01-15
Daniel,

The hardware and system configuration database would be most useful if it was done neutrally on a cross-distro basis. Maybe some kernel guy could write the harvester backend and simple frontends (for reviewing the data and adding comments) could be written in any preferred language, like curses or PyGTK, according to suitability. I'm not even suggesting Ubuntu should take responsibility of such undertaking all by itself.

What comes to the behind-the-scenes development, occasional updates and announcements would be most welcome here.

---

### Post by stoneguy on 2005-01-18
And the confusion continues to spread. See [http://www.ubuntuforums.org/showthread.php?p=50526](http://www.ubuntuforums.org/showthread.php?p=50526)

---

