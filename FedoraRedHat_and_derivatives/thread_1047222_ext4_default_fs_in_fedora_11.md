---
title: "ext4 default fs in fedora 11"
date: 2009-01-22
forum: Fedora/RedHat and derivatives
---

### Post by mariuz on 2009-01-22
> According to current plans, version 11 of Fedora, which is expected to arrive in late May, will use Ext4 as its standard file system

[http://www.heise-online.co.uk/news/Ext4-to-be-standard-for-Fedora-11-Btrfs-also-included--/112467](http://www.heise-online.co.uk/news/Ext4-to-be-standard-for-Fedora-11-Btrfs-also-included--/112467)

---

### Post by Circus-Killer on 2009-01-22
errr....okay.
if this was an attempt to convince people we need ext4 enabled in jaunty....doubt it will make too much difference. different distros make different decisions, thats what makes them different.

if this was an attempt to make conversation....i really have no way to respond to "fedora 11 is gonna use ext4" is by replying "okaaaaaay".

:popcorn:

---

### Post by AlexBellisBrown on 2009-01-22
Out of interest, if on release day, i was to upgrade to jaunty, will my filesystem remain ext3? Or will it change over to ext4? In order to change, would i be right in thinking i would have to reinstall Ubuntu fully?

---

### Post by autocrosser on 2009-01-22
You can convert your system over manually, you can opt to install as ext4 or you can just stay with ext3--we are having ext4 as a option until it settles down a bit more.....some people have been having data loss & that needs to be pinned down before it becomes the default.

---

### Post by int on 2009-01-22
1) Ext4 is a diferent filesystem. Not a a bug release of ext3.

2) The format of partion never change when we do one upgrade..
To change it, we have to change it manualy(converting, formating).

3) In Jaunty ext4 will not be the default choice..

4) You never have to reinstall Ubuntu fully when do one upgrade. (despite being recommended)

---

### Post by Archmage on 2009-01-22
Ehm...

According to current plans, version 9.04 of Ubuntu, which is expected to arrive in late April, will use Ext3 as its standard file system. However everyone can use Ext4 if he or she wants.

---

### Post by Simian Man on 2009-01-22
Fedora is always an early adopter.  Fedora 9 (May 2008) featured KDE4 (as the *only* KDE), and the new GDM which Ubuntu still doesn't use.  Fedora 10 features Plymouth, OpenOffice 3 and supposedly they almost made ext4 default for this release too (it was an option -- which I chose).  Fedora 11 is also going to include an option to use btrfs.

If you want to test out new, maybe buggy software Fedora is definitely the distro for you.  Ubuntu on the other hand aims at stability and user-friendliness so I doubt ext4 will be the default.

---

### Post by SlowJet on 2009-01-22
> **Simian Man said:**
> Fedora is always an early adopter.  Fedora 9 (May 2008) featured KDE4 (as the *only* KDE), and the new GDM which Ubuntu still doesn't use.  Fedora 10 features Plymouth, OpenOffice 3 and supposedly they almost made ext4 default for this release too (it was an option -- which I chose).  Fedora 11 is also going to include an option to use btrfs.

If you want to test out new, maybe buggy software Fedora is definitely the distro for you.  Ubuntu on the other hand aims at stability and user-friendliness so I doubt ext4 will be the default.

On the other hand, knowing the facts about EXT4 and why there was 2 or 3 times it had a missing piece would help those that what to use it get there with confidence rather that believing a few posters that have not installed with the latest bits.

I have used EXT4 in Fedora since 9.
There was only 3 times there was a problem.
1. The transition from k-25 to k26 - newly created (not install ) ext4 from k-25 would get zapped by the k-26 bits.

2. Two bug fixes for handling free space within the extend.

3. More EXT4 bits included in K-28 needed another fix in e2fsprogs.

I am much more concerned about the Debian installer using ext2 on thousands of /boot f/s. 
I can't tell you how many time the journal was used to recovery my systems and the /boot also.
It should be defaulted to ext3.

I also use LVM and SELinux and there is lots of horror stories there that have nothing to do with the facts.


SJ

---

### Post by Slug71 on 2009-01-22
C/P from Fedora's Website. Wish we had a features page!!

 >  Fedora 11 Accepted Features

These features have been accepted by the Fedora Engineering Steering Committee for the Fedora 11 Release.

Category:FeatureAcceptedF11
 % Complete 	Name 	Summary 	Updated
0% 	20 Second Startup 	Make Fedora boot and shut down faster. The goal is to be at the login screen in 20 seconds and be as fast as possible after the login (gnome-session). 	2008-12-17
80% 	Cups PolicyKit Integration 	Use PolicyKit to define policies for accessing the cups functionality 	2009-01-20
75% 	DeviceKit 	A simple system service to manage devices designed to partially replace hal and overcome some its design limitiations 	2009-01-21
80% 	DNS Security 	DNSSEC (DNS SECurity) is mechanism which can prove integrity and autenticity of DNS data 	2009-01-18
90% 	ext4 Default file system 	Make ext4 the default file system in Fedora 11 	2009-01-12
95 % 	Fingerprint 	Make fingerprint readers easy to use as secondary authentication 	2008-12-08
5% 	Gnome 2.26 	Rebase to Gnome 2.26 	2009-01-20
20% 	KDE4.2 	Rebase to KDE 4.2 and KOffice 2, and offer new features such as PolicyKit-KDE, NetworkManager plasma applet etc. 	2009-01-13
2% 	Multiseat 	Make it simple to configure a system for multiseat operation, where two or more users each have their own keyboard, monitor, and mouse, and can work independently of each other 	2008-11-18
90% 	Presto 	The presto plugin for yum adds support for downloading deltarpms and using them to generate new packages 	2008-09-09
45% 	Python 2.6 	Include Python 2.6 in Fedora 	2009-01-18
80% 	TightVNC 	Make TightVNC the default VNC client in Fedora 	2008-10-17
80% 	VolumeControl 	Make volume control intuitive and easy to use 	2008-12-08
20% 	Windows Cross-compiler 	Build and test full-featured Windows programs, from the comfort of the Fedora system, without needing to use Windows. 	2009-01-18
75% 	Xfce4.6 	Update Xfce to the upstream 4.6 release with many new improvements and features 	2009-01-19




So you can see Ext4 WILL be default in F-11.

---

### Post by SlowJet on 2009-01-22
Yes, and that means a /boot of ext3 with an LVM of 2 LV's for / and swap.
Mostly for newbies and mostly for expose ext4 more without the newbie knowing anything. Because it is Fedora. And the default install is not really a serious layout or upgrade path.

But the custom install dropdownbox on the installer allows whatever. Supposable even BTRFS will be in the F11 Alpha installer.

But when one is talking about converting ext3 to ext4, it depends on what (Kernel, e2fsprogs) and when (kernel 28.n newest e2fsprogs), and how(tunefs, debugfs options) you convert it.

SJ

---

### Post by Slug71 on 2009-01-22
> **SlowJet said:**
> Yes, and that means a /boot of ext3 with an LVM of 2 LV's for / and swap.
Mostly for newbies and mostly for expose ext4 more without the newbie knowing anything. Because it is Fedora. And the default install is not really a serious layout or upgrade path.

But the custom install dropdownbox on the installer allows whatever. Supposable even BTRFS will be in the F11 Alpha installer.

But when one is talking about converting ext3 to ext4, it depends on what (Kernel, e2fsprogs) and when (kernel 28.n newest e2fsprogs), and how(tunefs, debugfs options) you convert it.

SJ

You dont need a /boot of Ext3. Grub boots Ext4!
There are a bunch of us using Ext4 since it came to Jaunty and everything works fine.

If Jaunty has Kernel 2.6.29 it will also have Btrfs support possibly in the installer too.

Ext4 is NOW in Jaunty's installer. No need to convert.

---

### Post by inportb on 2009-01-22
> **Slug71 said:**
> Ext4 is NOW in Jaunty's installer. No need to convert.

True only if you're wiping everything and starting over. Those of us who have ext3 partitions that we want to keep have to convert them after installation, but that's pretty easy to do.

---

### Post by Slug71 on 2009-01-22
> **inportb said:**
> True only if you're wiping everything and starting over. Those of us who have ext3 partitions that we want to keep have to convert them after installation, but that's pretty easy to do.

True,
You should however have everything backed up though and be ready for a reinstall as Jaunty is still in Alpha and there is a possibility for serious breakage.
And i could be wrong but i think some features are left out by converting.

---

### Post by bruce89 on 2009-01-22
Yet again Fedora innovates, Ubuntu prevaricates.

---

### Post by Slug71 on 2009-01-22
> **bruce89 said:**
> Yet again Fedora innovates, Ubuntu prevaricates.

Jaunty was mainly gonna be a bug fix and boot performance increase release from the start though.
For 9.10 we'll have Plymouth and Login Experience/Facebrowser though.
And Packagekit if we dont have it for Jaunty.
Hopefully Anaconda too.

---

### Post by RAOF on 2009-01-22
> **bruce89 said:**
> Yet again Fedora innovates, Ubuntu prevaricates.

For definitions of "innovates" equal to "uses much less tested technology by default".  I, for one, am very happy that we choose our *default* filesystem very conservatively, while retaining the ability for users who care to choose a more risky filesystem.

I'm very glad that Red Hat employs many infrastructure developers.  It's great that they aggressively push that technology out to testing.  But "agressively push technology out to testing" and "create an environment that Just Works" are goals with a significant component of competition - you really can't do both.  If you want to be closer to the bleeding edge, perhaps Fedora *is* a better fit for you.

Ubuntu doesn't have to be Fedora.  Ubuntu doesn't *want* to be Fedora.

---

### Post by bruce89 on 2009-01-22
> **Slug71 said:**
> Jaunty was mainly gonna be a bug fix and boot performance increase release from the start though.
For 9.10 we'll have Plymouth and Login Experience/Facebrowser though.
And Packagekit if we dont have it for Jaunty.
Hopefully Anaconda too.

All of which were in Fedora ages ago. Also, I can't help noticing the fact that in the past they said PackageKit would be in Intrepid.

One thing I'd really like is the new GDM.

---

### Post by Slug71 on 2009-01-22
> **bruce89 said:**
> All of which were in Fedora ages ago. Also, I can't help noticing the fact that in the past they said PackageKit would be in Intrepid.

One thing I'd really like is the new GDM.

They don't have Login Experience/Facebrowser.
I dont know whats up with Packagekit though.

Really wish we had something like this though:

[https://fedoraproject.org/wiki/Releases/11/FeatureList](https://fedoraproject.org/wiki/Releases/11/FeatureList)

Would stop so many of the same questions from being asked here and answer a lot of our questions.

---

### Post by SlowJet on 2009-01-23
> **Slug71 said:**
> You dont need a /boot of Ext3. Grub boots Ext4!
There are a bunch of us using Ext4 since it came to Jaunty and everything works fine.

If Jaunty has Kernel 2.6.29 it will also have Btrfs support possibly in the installer too.

Ext4 is NOW in Jaunty's installer. No need to convert.

I was referring to the Fedora default install as that is the name of the thread.

And it looks like all the scare tactics about ext4 are all about bad disk drive firmware.

Like I said, there was only a few bugs about zero bytes caused by non recovered freespace in the extents.

There has not been any new bugs in ext4 found since the last e2fsprogs was released. And frankly ext4 on a /boot f/s buys very little.

SJ

---

### Post by Eclipse. on 2009-01-23
> **bruce89 said:**
> Yet again Fedora innovates, Ubuntu prevaricates.

First off upstream does the innovation, distros just pick and choose what they want.RAOF pretty much said everything I was going to but what I will add is alot of people dont realise that fedora is only Red Hat's playground for RHLS.This allows them to push the boat out and have the latest and greatest of everything.The prime example is EXT4, yes theres some bugs but that doesnt matter for Fedora where as with us its important that the file systems is 100% _very_ stable.

PS Slug: Grub only works with EXT4 because its been patched.

---

### Post by bruce89 on 2009-01-23
> **Eclipse. said:**
> First off upstream does the innovation, distros just pick and choose what they want.RAOF pretty much said everything I was going to but what I will add is alot of people dont realise that fedora is only Red Hat's playground for RHLS.This allows them to push the boat out and have the latest and greatest of everything.The prime example is EXT4, yes theres some bugs but that doesnt matter for Fedora where as with us its important that the file systems is 100% _very_ stable.

Indeed upstream does the work, but Fedora actually have a big part in upstream work, unlike Ubuntu.

---

### Post by gnomeuser on 2009-01-23
> **Eclipse. said:**
> First off upstream does the innovation, distros just pick and choose what they want.RAOF pretty much said everything I was going to but what I will add is alot of people dont realise that fedora is only Red Hat's playground for RHLS.This allows them to push the boat out and have the latest and greatest of everything.The prime example is EXT4, yes theres some bugs but that doesnt matter for Fedora where as with us its important that the file systems is 100% _very_ stable.

PS Slug: Grub only works with EXT4 because its been patched.

Fedora does a lot of work upstream, many of the Fedora developers are maintainers of parts of the kernel, the tool chain as well as the X stack and GNOME. Innovation does happen in Fedora, we just choose to do it upstream.

Additionally, more people now work on Fedora who are not on Red Hat payroll than people who are. It is not the RHEL playground you claim, Red Hat elects to base their products on Fedora but it is a community driven project. I myself work on Fedora without taking a penny from RH. Red Hat does allow their employees to spend 20% of the time on personal projects, many elect to work on Fedora during this time, however the Fedora community now encompasses aside many skilled volunteers such companies as Dell, Intel and AMD. The steering committee and the Fedora Board are both comprised of more community people than Red Hat appointed members. We all shape Fedoras future together.

If Fedora is anything label worthy it's a technology engine, we produce and put innovative technology into the hands of people.

[http://fedoraproject.org/wiki/PackageMaintainers/WhyUpstream](http://fedoraproject.org/wiki/PackageMaintainers/WhyUpstream)

---

### Post by plun on 2009-01-23
Fedora, Fedora, Fedora.....

What do you want with this never ending Fedora talk  ????

---

### Post by BCurtisWX on 2009-01-23
> **bruce89 said:**
> Indeed upstream does the work, but Fedora actually have a big part in upstream work, unlike Ubuntu.

I think MS is trying to do more.. Hence him hiring more people to work on different part of ubuntu.

---

### Post by SlowJet on 2009-01-23
> **plun said:**
> Fedora, Fedora, Fedora.....

What do you want with this never ending Fedora talk  ????

Hey plun, didn't you get the word that thread squashes have been re-listed BELOW exit speeches. lol

SJ

---

### Post by bruce89 on 2009-01-23
> **plun said:**
> Fedora, Fedora, Fedora.....

What do you want with this never ending Fedora talk  ????

Because of the thread's title perhaps.

> **BCurtisWX said:**
> I think MS is trying to do more.. Hence him hiring more people to work on different part of ubuntu.

Mark only cares for forking things for Ubuntu's sole use. Also, he thinks he seems to think he controls FOSS (he e-mailed the GNOME people telling them to switch to Qt, and they just said "Who are you to tell us what to do").

---

### Post by Gourgi on 2009-01-23
> **bruce89 said:**
>  Also, he thinks he seems to think he controls FOSS (he e-mailed the GNOME people telling them to switch to Qt, and they just said "Who are you to tell us what to do").

provide a link to that mail please

---

### Post by bruce89 on 2009-01-24
> **Gourgi said:**
> provide a link to that mail please

[http://gnome.markmail.org/search/?q=shuttleworth#query:shuttleworth+page:2+mid:lxazwmlis6thd3iz+state:results](http://gnome.markmail.org/search/?q=shuttleworth#query:shuttleworth+page:2+mid:lxazwmlis6thd3iz+state:results)

Apparently GNOME's migration to git was delayed on Mark's request. - [http://gnome.markmail.org/search/?q=shuttleworth#query:shuttleworth+page:2+mid:gdpagkjmnaqqzgmn+state:results](http://gnome.markmail.org/search/?q=shuttleworth#query:shuttleworth+page:2+mid:gdpagkjmnaqqzgmn+state:results)

---

### Post by zekopeko on 2009-01-24
> **bruce89 said:**
> 
Mark only cares for forking things for Ubuntu's sole use. Also, he thinks he seems to think he controls FOSS (he e-mailed the GNOME people telling them to switch to Qt, and they just said "Who are you to tell us what to do").

my my aren't you a good little troll. shuttleworth didn't send any mail to the gnome list telling them to switch. he said in an interview that it *could be possible to use Qt* for future Gnome.

and he didn't request them to postpone the switch to some form of DVCS.
read YOUR links more careful before posting.

---

### Post by gjoellee on 2009-01-24
> **AlexBellisBrown said:**
> Out of interest, if on release day, i was to upgrade to jaunty, will my filesystem remain ext3? Or will it change over to ext4? In order to change, would i be right in thinking i would have to reinstall Ubuntu fully?

Even if you had Ext2 in your Ubuntu installation now and upgraded to Jaunty you would still have Ext2. Jauntys default file system will stay as Ext3 by default, but Ext4 by option. If you want Ext4 you can convert your existing Ext3 file system. Or you can install the system again, and do a manual partition.

---

### Post by bruce89 on 2009-01-25
> **zekopeko said:**
> my my aren't you a good little troll. shuttleworth didn't send any mail to the gnome list telling them to switch. he said in an interview that it *could be possible to use Qt* for future Gnome.


Yes, I admit I got it wrong, but there's no need to start insulting people.

---

### Post by Vince4Amy on 2009-01-26
Hopefully they may add JFS to the livecd. I have to download the DVD image each time in order to install Fedora with JFS.

---

