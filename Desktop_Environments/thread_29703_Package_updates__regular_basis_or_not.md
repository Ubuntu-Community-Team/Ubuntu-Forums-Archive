---
title: "Package updates:  regular basis or not?"
date: 2005-04-25
forum: Desktop Environments
---

### Post by GTKpower on 2005-04-25
OK, this is VERY confusing for me, so please be patient.  ;)

I'm currently under the impression that the repoistories are NOT updated with new (updated) packages on a regular basis. 

Since we have access to these massive repositories, whether you're running Warty or Hoary, certain packages should be updated on a regular basis.  This is normal.  By "regular basis" I mean, say, if Firefox 1.xx comes out the first week of June, we'll see the package show up around third week, maybe fourth.

This keeps things nice and bleeding-edge.  With all due respect to the developers of Ubuntu, who have given us a wonderful distro, I certainly hope that we're not made to wait for a whole distro upgrade to get updated packages.  That would be ridiculous, and to be honest, unacceptable.  It would be something that would be a big deal-breaker between myself and Ubuntu.  Again, I do not mean to be obnoxious or rude here - I have plenty of respect for developers who can keep any distro at  #1 in the Distrowatch rankings, but if there's a whole team with enough reources available, we should be seeing updated packages in the repositories in a timely manner.  

Yes, one CAN install from source or right off the web, but the point is we DO have repositories that ensure dependencies are met.  We just saw how much of a pain it is to install off the web.  Repositories are there.  They need to be used.  It is my policy to NOT install from the web, for good reason.  

I came to Ubuntu from PClinuxOS.  There was ONE GUY (Texstar) and *maybe* another, updating packages, preparing them, and posting them on to the repositories.  They resided in the "unstable" section for a short while (to which users had complete, easy access), and were moved to the "stable" section in a very timely manner.  For instance, we were getting amaroK updates once a month, t least.

I hope my comments aren't taken the wrong way.  If my assumptions are mistaken, then I offer my sincere apologies.

---

### Post by GTKpower on 2005-04-25
I guess the asnwer lies in visiting the Breezy repositories?  Is that where updates can be found regularly?  I've got them loaded now and I see an Evolution update already.

---

### Post by denzilla on 2005-04-25
I'm not so sure you should be updating from the Breezy repos as they may be highly unstable. I do agreee with your idea on updates, though. At the very least, Firefox, OpenOffice and bugfixes should be updated on a regular basis until the support cycle for a distro is up.

---

### Post by GTKpower on 2005-04-25
[QUOTE=denzilla]I'm not so sure you should be updating from the Breezy repos as they may be highly unstable. I do agreee with your idea on updates, though. At the very least, Firefox, OpenOffice and bugfixes should be updated on a regular basis until the support cycle for a distro is up.[/QUOTE]

Right.  But there do seem to be updates to some key apps in the Breezy repositories, such as Gaim, Graveman, Evolution (though it wants to remove my existing version oe evolution), and some others.

I'm not looking to doa complete upgrade by this, just update some key apps.

In any case, I don't mean to come off sounding like an ungrateful jerk, but it would be nice if ther core apps that came with Ubuntu were kept bleeding-edge.

Thanks for replying, by the way.

---

### Post by denzilla on 2005-04-25
np :)  


I think they get the update ideals from the debian gang. I'm a noob, so just going from what I read off posts.

---

### Post by nix4me on 2005-04-25
Well, i think they should consider any upgrade to firefox critical.  I am very disappointed at the lack of a Firefox 1.0.3.  Any update to a application that is responsible for communicating with the internet should be done.

I guess the Ubuntu developers are picking and choosing which updates they deem critical.

Mark

---

### Post by GTKpower on 2005-04-25
Well I hope they're not TOO wedded to Debian ideals.  

There is a school of thought that says Debian's release/update cycles are hurting it.  I tend to believe this.

In any case, I think it would be very reasonable for updates to come every 3-4 weeks, if there are updates to be had in that timeframe.    That gives enough time, I should think, to package the truly mission-critical apps and get them ready.  Not too many, just the ones that CAME with Ubuntu, if even that.  For example, if Firefox 1.xx comes out on June 1st, it would be nice to see it appear in the repos by July 1st.  Sure, I'd like it sooner, but developing/maintaining Ubuntu is alot of work.  Let's be fair.

OpenOffice
Gaim
Rhythmbox
Soundjuicer
Firefox
Evolution
 . . .  and a few more I'm missing,
+ dependencies, obviously

Does that sound reasonable?

Still, unless I'm mistaken, is this not what is happening in the Breezy repos?  I've already updated Gaim and a few other apps from there . . . I'd imagine new versions of Firefox and whatever else will be thre soon.  No?

---

### Post by tomchuk on 2005-04-25
Rolling updates are not without their problems. Anyone who has run Debian unstable for any period of time can tell you the problems you run into. running apt-get upgrade and seeing a new major version of libc6 is always a fun experience.

Say there's a new version of rhythmbox and you want it installed. New rhythmbox is built on new gstreamer libs - there's 45 packages that need to be updated. And at least 100 that also need to be QA'd with the new gstreamer version. Backporting rhythmbox to work on the old gstreamer libs is possible, but wouldn't you want the devs concentrating on getting it working with the *new* libs so that it works in Breezy? The point of a "release" is that it's released - develoment efforts are concentrated on the development version and only critical updates are supplied to the release version.

In short it's just too much of a mess on a binary distro. This works in Gentoo because you're building new software on what is on your system at the moment. Rebuilding world overnight, will effectively stabilize your system to a sort of "release"  - everything is built against current versions of everything else and everything is happy.

I'd rather deal with a very slightly out of date system for 6 months that is properly QA'd and works than a perpetually bleeding-edge system in a state of perpetual brokenness. If you want bleeding-edge that what backports are for :)

---

### Post by fng on 2005-04-26
There wont be any hoary updates except security fixes or critical bug fixes.

If you want more bleeding edge packages, try out the hoary backports (3rd party projects on the forum).  Those are newer packages from breezy or debian/sid, compiled for hoary.

---

### Post by Leif on 2005-04-26
If there are security bugs that are addressed in firefox 10.3, these will be implemented for hoary and updated. It might not be called 1.0.3, maybe 1.0.2ubuntux, but afaik security vulnerabilities get addressed. If the update is not critical, it will not be implemented until breezy comes out. 

As long as security is maintained, I'd rather have a stable distro with a 6-month cycle than bleeding-edge which will go pear-shaped every once in a while. Plus, you can always ask the nice people at the backports project.

---

### Post by GTKpower on 2005-04-26
How can I access the bkacports?  Do I add it to my repository list?

---

### Post by shakin on 2005-04-26
You can think of the main Hoary repositories as an ISO. When you download, say, Fedora Core 3 you get the same distro whether you download it now or in a month. The one exception is that Ubuntu will get security updates.

Ubuntu delivers new versions through the backports or next version (Breezy) repositories. So, go add Breezy and you have your updates. I think this is an acceptable solution, although not perfect since things will sometimes break. Don't do a dist-upgrade from Breezy until it's more stable.

---

### Post by gbusse on 2005-04-26
GTK Power,

To add backports to your apt sources, look at this page:

[http://ubuntuguide.org/#backportsrepositories](http://ubuntuguide.org/#backportsrepositories)

Firefox 1.0.3 is in there now as well as some other stuff too...

Gord

---

