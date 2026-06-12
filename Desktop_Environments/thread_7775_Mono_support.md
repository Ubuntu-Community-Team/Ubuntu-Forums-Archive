---
title: "Mono support"
date: 2004-12-11
forum: Desktop Environments
---

### Post by frankps on 2004-12-11
Hi,

I miss support for several applications in ubuntu. 

I would like to see a mono package for ubuntu (also the x86-64 version).

I know that [Beagle](http://www.gnome.org/beagle/) is in an early stage of development, but there are also other interesting projects that make use of mono:

1- [MonkeyPop](http://mspace.berlios.de/gunther-user/view.php/page/MonkeyPop) 


[IMG]http://mspace.berlios.de/gunther-user/uploads/pages/MonkeyPop-Scripts/full-shot-big.png[/IMG]

2 - After having read this [article](http://www.oreillynet.com/pub/a/network/2004/10/18/mono.html), there are two other applications that I also would like to see : [Muine](http://muine.gooeylinux.org/) and [Blam!](http://www.imendio.com/projects/blam/)

Are there other cool Mono based applications that users would like to see on ubuntu?

---

### Post by nzgreen on 2004-12-11
[Monodevelop](http://www.monodevelop.com/) could come in handy.

---

### Post by jdong on 2004-12-11
Ubuntu already has Mono, in Universe. It's version 1.0.0 or 1.0.1, if I remember. I've asked in #ubuntuforums if they'd be interested in seeing a backport of a newer Mono, but they said the current version runs everything they want.


As for the other apps..... I might package them as Ubuntu extras, but that'll depend on how much time I have!

---

### Post by frankps on 2004-12-12
Thanks for the answer jdong. Will try it out. I have promised my self to forget about Beagle after having tried to install it on a SUSE installation yesterday without success. But I managed to install the other software and I can't say other than I liked them.

I will install ubuntu on my laptop too and upgrade that one to hoary, and keep my desktop computer with only stable releases for work. 

I found this thread in the hoary section of the forum:
[http://www.ubuntuforums.org/showthread.php?t=7758](http://www.ubuntuforums.org/showthread.php?t=7758)

I will try to install Mono on the Hoary release.

---

### Post by jdong on 2004-12-14
Hmm, after a bit of thought and testing of Mono in Warty, I have decided to backport the latest **stable/production** release of mono and its accompanying libraries over to Warty... That includes Monodevelop 0.5.1.

Stay tuned for details.

---

### Post by frankps on 2004-12-20
Hi again,

I have followed to Beagle-HowToInstall-Wiki - [http://www.ubuntulinux.org/wiki/BeagleInstallHowto/view?searchterm=beagle](http://www.ubuntulinux.org/wiki/BeagleInstallHowto/view?searchterm=beagle) - and gotten all the way down to actually downloading and compiling Beagle.

Some errors occurs in this compiling process and it stops up:

./TilePicture.cs(52) error CS1502: The best overloaded match for method 'string Beagle.Images.GetHtmlSource (byte[], string)' has some invalid arguments
./TilePicture.cs(52) error CS1503: Argument 0: Cannot convert from 'System.Uri' to 'byte[]'
./TilePicture.cs(52) error CS1501: No overload for method `GetHtmlSource' takes `2' arguments
./TilePicture.cs(52) error CS8006: Could not find any applicable function for this argument list
Compilation failed: 4 error(s), 0 warnings
make[2]: *** [Tiles.dll] Error 1
make[2]: Leaving directory `/home/frankps/cvs/beagle/Tiles'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/frankps/cvs/beagle'
make: *** [all] Error 2
root@ubuntu-lappie:/home/frankps/cvs/beagle #

I hope somebody can help me today, so that I can take my laptop with ubuntu and fully working Beagle with me home for the Christmas weekend.

---

### Post by Quest-Master on 2004-12-20
Ah, MonkeyPop!

I've been looking for something like this for so long. Do you have to code notifications in X-Chat and Gaim on your own though? Or does it have plugins for them?

---

### Post by randy on 2004-12-22
Are you building Beagle from cvs?  If you are just update your cvs archive and try again.

---

### Post by frankps on 2004-12-22
Yes, I tried resyncing the next day, about 8 hours later. 

I had the same problems.

I will try doing it after christmas.

Thanks for trying to help :-)


Frank

---

### Post by macewan on 2004-12-28
[QUOTE=frankps]Yes, I tried resyncing the next day, about 8 hours later. 

I had the same problems.

I will try doing it after christmas.

Thanks for trying to help :-)


Frank[/QUOTE]
 frankps,

are you trying for warty or is it on a box that has been switched to hoary?

---

### Post by frankps on 2004-12-29
Yes, I am.

Upgraded both my desktop x86-64 and laptop x86 to hoary.

The laptop has mono installed, but did not manage to install Beagle by following the wiki, same goes to Monkey Pop, and I couldn't upgrade to newly released versions of Muine and Gossip.

When it comes to the x86-64. I have not been able to install Mono through apt-get. I simply haven't find all the needed files.

Beagle is essential for me, having lived with BeOS for 5-6 years, and now Zeta. Monkey Pop would have been cool. I am using something similar under Zeta, called InfoPopper and love it.


Frank

---

### Post by daniels on 2004-12-29
Mono doesn't run under amd64, IIRC.

---

### Post by frankps on 2004-12-30
Thanks for letting me know Daniel.

Just that there were some mono related packages available.

---

### Post by ernstp on 2005-01-17
[QUOTE=daniels]Mono doesn't run under amd64, IIRC.[/QUOTE]

Hmm, you don't. :-)
Is that the only reason why there is no mono for AMD 64 in hoary?

The development version even has a JITC for amd 64.

---

### Post by frankps on 2005-01-29
I switched to Hoary, but this week there came smoke up from the keyboard and it wasn't cause of my fast writing.

I will get a new laptop soon and only have a x86-64 desktop system at the moment.

---

### Post by Reb on 2005-03-02
Get (the new version of) Mono (1.1.4) (with amd64 support), and all your wildest dreams will come true!

---

