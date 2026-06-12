---
title: "KDE4 beta 4"
date: 2007-11-01
forum: Desktop Environments
---

### Post by michaelmartin003 on 2007-11-01
We have now the kde4 beta 4 in the Debian repository.

[http://pkg-kde.alioth.debian.org/kde4livecd.html](http://pkg-kde.alioth.debian.org/kde4livecd.html)

This is a Debian live CD with the kde4 3.95. Now the task bar works. I am thinking now, for first time, it is possible to use it because till now it was more close to an alpha version that a beta.

Kubuntu has still no kde4 beta 4 in it's own repositories. I don't recommend to install kde4 from the rpm repositories of OpenSUSE. It's better waiting for kubuntu's. 

An idea for installing kde4 beta 4 is with a package manager called "smart". With it is possible installing in the same distribution, in our case ubuntu, packages of dpkg/rpm. 
I am now in a computer with no ubuntu, so I don't know if it's possible finding smart in synaptic or adept. The web where is possible to download it is this:

[http://packages.debian.org/unstable/source/smart](http://packages.debian.org/unstable/source/smart)

I rode this about smart:

"The Smart Package Manager project has the ambitious objective of creating smart and portable algorithms for solving adequately the problem of managing software upgrading and installation. This tool works in all major distributions, and will bring notable advantages over native tools currently in use (APT, APT-RPM, YUM, URPMI, etc)." [http://labix.org/smart](http://labix.org/smart)

Well. Now that we can install rpm packages in ubuntu we need the sources for the packages of OpenSUSE kde4. The web where repositories are is this:

[http://en.opensuse.org/Package_Repositories#KDE_4](http://en.opensuse.org/Package_Repositories#KDE_4)

I downloaded a file of the OpenSUSE 10.3 version repository for KDE4 and the lines inside are that:

[KDE:KDE4]
name=KDE 4 development version builds (openSUSE_10.3)type=rpm-md
baseurl=http://download.opensuse.org/repositories/KDE:/KDE4/openSUSE_10.3/gpgcheck=1
gpgkey=http://download.opensuse.org/openSUSE-Build-Service.ascenabled=1

I didn't try because I think it's dangerous mixing packages of dpkg and rpm. With Smart package manager it is possible. Maybe Smart could make then to get KDE4 beta 4 from OpenSUSE repository, notwithstanding I think it's better waiting for kubuntu.

---

### Post by Caffeine_Junky on 2007-11-01
Sure, you can use what ever you want too :)

I would not touch it untill it is in it's Final Release (personally)

...which ever way you look at it Beta is still Beta (obviously)

Good luck.

---

### Post by omschaub on 2007-11-01
I just tried the opensuse live cd with this beta on it and I have to admit, it is really smooth.  Still a few issues here and there, but all in all, very usable.  I feel that if I could get it into my ubuntu without breaking anything, I would certainly enjoy trying it out.  I am hopefull that by the time a release candidate is out, we will have official support for testing it.

---

### Post by susi on 2007-11-01
I add those two lines in sources.list, but I don't know what packages are beta 4. I have only beta 3 packages from kubuntu repos.

---

### Post by Pay87 on 2007-11-01
Is there anybody running Beta 4 successfully atm? I dont know how to get this working :(

---

### Post by vikramsharma on 2007-11-02
I am getting the gpg key error anyone knows where to get the gpg key for the repositories mentioned above.  Thanks in advance.

---

### Post by wieman01 on 2007-11-02
> **vikramsharma said:**
> I am getting the gpg key error anyone knows where to get the gpg key for the repositories mentioned above.  Thanks in advance.
No idea where you would get them from, but you don't really need them to install stuff.

---

### Post by jlacroix on 2007-11-02
Why aren't there any Kubuntu packages yet?

---

### Post by Pay87 on 2007-11-02
Thats very bad, i would really like to test it, because i cant run Beta 3..
/edit:
I managed to run Beta 3 but it is totally useless for Kubuntu..
It looks more like a Alpha.
Hopefully there will be packages for Beta 4 soon!

---

### Post by lexxonnet on 2007-11-03
I'm quite looking forward to seeing beta 4 in the repos as well. I installed the packages in the kubuntu repos yesterday, and most of them are beta3, some are beta 2(artwork,network,utils), and some are even beta1(addons,toys)!

I can get into the session, and kickoff exists as a separate application, but the desktop itself doesn't look beta3, cos the suse live cd definitely had a semi-working kickoff, and a different desktop-toolbox button.

Anyway, the packages aren't unusable as some people claim... just a little complicated!

---

### Post by LuisAugusto on 2007-11-04
Pardon me?

Kubuntu KDE 4 packages always sucks, OpenSUSE packages are inmensly better, and they contain more modules.

As you said, SMART does support rpm and dpkg backends, but, that doesn't mean you can use your OpenSUSE repos in Kubuntu or inverse. 

The best way to test KDE 4 packages is to use Debian or OpenSUSE.

---

### Post by Wiebelhaus on 2007-11-04
oddly enough , if you've ever IM'd or been on Voip with me you'd know , I'm a flaming hell fire & brimstone Gnome freak , But I like this , it's not bad at all.

---

### Post by pacodani on 2007-11-07
I wonder: isn't Kubuntu one of the main platforms to test with kde4 beta? I think so, so I don't understand why kde4 beta4 is out of repositories today. I have installed it in my other gentoo box in order to test and submit bugs. 

For me, 0 points for kubuntu today.

Salut!

---

### Post by SteFaNweI on 2007-11-07
agreed!
i do not understand why _k_ubuntu still has no packages - it is more than one week ago that beta4 was launched... when packages come up it might already be the time of beta5 or rc1.

p.s.: i know that the ubuntu-devs are currently busy with their summit and the next release but i think this is not an excuse for such a long delay.

---

### Post by lexxonnet on 2007-11-07
Hmm... I'm quite puzzled as well as to why there are no beta4 packages... 

I remember switching to Kubuntu because of the promise of constantly updated kde packages on a 6-monthly stable system. I might give debian unstable a try and see how it goes, because kubuntu has been lagging a bit of late.

---

### Post by maybeway36 on 2007-11-07
The Debian KDE maintaners have a KDE 4 live CD.
[http://pkg-kde.alioth.debian.org/kde4livecd.html]("http://pkg-kde.alioth.debian.org/kde4livecd.html")

---

