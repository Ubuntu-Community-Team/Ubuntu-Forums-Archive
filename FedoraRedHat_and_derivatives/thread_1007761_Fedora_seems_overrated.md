---
title: "Fedora seems overrated"
date: 2008-12-10
forum: Fedora/RedHat and derivatives
---

### Post by ryaxnb on 2008-12-10
Fedora is an interesting distro. They contribute a lot of code to Linux projects. And of course they are sponsored by on of the biggest linux companies, Red Hat. But they seem to lack direction. Some releases are really good and some are really bad. 

Bad:
Fedora has uneven releases
Fedora is often unstable
Fedora lacks a good distro-updating mechanism
Fedora uses a so-so package manager (zypper, smart, aptitude, pacman and urpmi are all arguably better)
Fedora is completely 3d and multimedia incapable OOTB, though this can be fixed with some difficulty (and for those who consider this a plus, remember there are still several binary blobs in the kernel and such.)
Fedora is only OK at the UI IMHO
Good:
Fedora is bleeding-edge without being hard to install, like Arch or Debian Sid is.
Fedora is highly-RPM compatible. Overall, the Red Hat system is the most common one for RPMs - in other words, most RPMs are tailored for RedHat/Fedora. Whether incompatible (e.g. older version, RHEL RPMs) or tailored for that version, it is rather likely they'll be compatible compared to other RPM distros.
RPM is still the leading format for many non-oss and obscure FOSS and outdated programs,and thus Fedora picks up quite a library of compatible binaries. Furthermore, most configure files expect fedora as a possible compiling host.
Fedora is similar to RHEL, and LSB-compliant. Oh, and the artwork is sometimes quite nice.
That's about it for the good. 
There really isn't much to say about fedora. To me, [almost] everything about it screams mediocre. Support for non-GNOME desktops? Mediocre. Support for hardware that isn't used in servers? Mediocre. UI? Mediocre. PKG management? Mediocre. Support for 3d accel or codecs or MS Active Directory etc? Poor to mediocre. Stability and release-to-release stability? Mediocre.

So why is it still popular?

---

### Post by igknighted on 2008-12-10
> **ryaxnb said:**
> Fedora is an interesting distro. They contribute a lot of code to Linux projects. And of course they are sponsored by on of the biggest linux companies, Red Hat. But they seem to lack direction. Some releases are really good and some are really bad. 

Bad:
Fedora has uneven releases
Yes: 1, 3, 5, 7 and 9 were all odd, and not even.  

> **ryaxnb said:**
> Fedora is often unstable
They do aim to  provide the most up to date software available, so a little instability goes with the territory.

> **ryaxnb said:**
> Fedora lacks a good distro-updating mechanism
Actually, preupgrade is the best version upgrade tool available for any distro (short of being rolling release).  Yes, this is opinion, but they took a completely different approach and I think it will prove over time to be the best option.

> **ryaxnb said:**
> Fedora uses a so-so package manager (zypper, smart, aptitude, pacman and urpmi are all arguably better)
Smart can be used with Fedora, but I can't think of a single reason why apt is better.  And YUM has the absolute best terminal output of any package manager, and that is not trivial.

> **ryaxnb said:**
> Fedora is completely 3d and multimedia incapable OOTB, though this can be fixed with some difficulty (and for those who consider this a plus, remember there are still several binary blobs in the kernel and such.)
My 3d (intel chip) worked out of the box.  Almost all ATI cards will work out of the box with radeonhd.  Nvidia and fglrx can be installed/enabled by going to the rpmfusion website, enabling the repo there, and then 'yum install <packagename>.  Hardly difficult.  Also, there is a custom spin available with these things enabled (think mint for fedora).  Multimedia is just as simple.

> **ryaxnb said:**
> Fedora is only OK at the UI IMHO
Regardless of whether you like the artwork used, gdm2 and plymouth are great advancements for the future.  Beyond that they really don't do anything special that others don't.

> **ryaxnb said:**
> Good:
Fedora is bleeding-edge without being hard to install, like Arch or Debian Sid is.
To be fair to other distros, Sidux (debian sid) is more up to date, and almost as easy to use/install.

> **ryaxnb said:**
> Fedora is highly-RPM compatible. Overall, the Red Hat system is the most common one for RPMs - in other words, most RPMs are tailored for RedHat/Fedora. Whether incompatible (e.g. older version, RHEL RPMs) or tailored for that version, it is rather likely they'll be compatible compared to other RPM distros.
true, but I would say using pre-built debs or rpms from non-distro specific sources is very rare.

> **ryaxnb said:**
> RPM is still the leading format for many non-oss and obscure FOSS and outdated programs,and thus Fedora picks up quite a library of compatible binaries. Furthermore, most configure files expect fedora as a possible compiling host.
Perhaps the first part is true, but that can be worked around.  But configure files should be pretty universal.

> **ryaxnb said:**
> Fedora is similar to RHEL, and LSB-compliant. Oh, and the artwork is sometimes quite nice.
That's about it for the good. 
There really isn't much to say about fedora. To me, [almost] everything about it screams mediocre. Support for non-GNOME desktops? Mediocre. Support for hardware that isn't used in servers? Mediocre. UI? Mediocre. PKG management? Mediocre. Support for 3d accel or codecs or MS Active Directory etc? Poor to mediocre. Stability and release-to-release stability? Mediocre.

You have made a lot of very broad statements without really any evidence to back them up.  Mediocre non-gnome support?  Tell that to Fedora's KDE team.  I think almost everyone would tell you Fedora's KDE spin is light years better than Ubuntu's.  Support for non-server hardware?  Umm... well, they got pulseaudio to work great, that's not server related (ok, you got me... it is an audio server :P).  I have time and again had major hardware compatability issues with Ubuntu, only to have it work with Fedora.  And if it didn't work right away, Fedora fixed it in an update, while Ubuntu did not.  UI and Package management are complete opinions, many will agree with you and many will disagree.  Their 3d support was poor in Fedora 9 due to the use of the latest Xserver, which ATI refused to make a driver for, and beyond that they seem to do just fine.  I don't see hoardes of others complaining.

I'd be happy to refute your points more, but I think you get the idea.

You mentioned the direction early in your post, and I think in the past few releases they have found found that direction.  Remember, the distro is about as old as Ubuntu, but Ubuntu was formed with a definite goal.  Fedora was cut free from Red Hat and had to find itself.  Since about Fedora 7 or 8, they have really figured it out.  Read the fedora project's website and you will understand.

---

### Post by Sorivenul on 2008-12-11
I tend to disagree.

Fedora and Ubuntu have different philosophies regarding software. The same can be said for Fedora vs many other distributions.  

These differences take some adjustment, much like users switching to Linux systems from Windows or OSX. Whether out of the box or not, Fedora can be configured just like any other distribution. 

I personally think that yum/PackageKit are underrated. I agree with the previous statement that yum produces some of the best terminal output of any package management system.  But, the "package management war" has been raging for a long time, and this small factor doesn't make a distribution - philosophy does.

Fedora's odd numbered releases have felt more unstable than their even numbered releases, but are still usable. 

Their current KDE release in Cambridge rivals that of any other KDE implementation I've tested, including OpenSUSE, which previously had my nod of approval.

The vast array of third-party repositories like RPMfusion (which is made up of the three previously most popular third-party repositories), is a testament to Fedora's popularity.  There are many interesting usage statistics floating around for Fedora, and an interesting article was recently written regarding this subject on DistroWatch Weekly.

In another thread on these forums about Fedora it was said that Fedora feels like a more "grown-up" distribution, and with this, I would agree.  Like its "bleeding-edge" nature, the thought that goes into the simplicity of Fedora is often ahead of its time.  

I could go on, as I personally love Fedora, especially the recent release.  Other user's mileage may vary.

---

### Post by tcoffeep on 2008-12-11
With the machines I've used Fedora on, it wouldn't run as smoothly as, say, Ubuntu or Arch, so I have a negative view of the distro. But, hey, what works for others works, right?

---

### Post by ibutho on 2008-12-11
As others have mentioned, Fedora has a different philosophy to Ubuntu when it comes to software. Many of their releases are bleeding edge and sometimes include experimental features. Obviously this results in some releases being better than others. Ubuntu is similar in a way, some releases are good and others are bad. 

As for updating, you can use yum to update from one release to another. I have done it myself on a couple of occasions and didn't face any major problems. For the 3D and multimedia stuff, you can install all the required packages from the rpmfusion repository. In Fedora 10, yum seems to have been improved a lot and to me it works just as good as apt, zypper and others.

---

### Post by y6FgBn)~v on 2008-12-11
The new packageKit feature is nice. If you try to open for example a media file and dont have the proper codec installed, it will ask you if you would like to install the codec. I tried the xfce spin live cd but ran into a few problems with my particular hardware.

---

### Post by thewOndErEr57 on 2008-12-11
Yes,

PackageKit is a great addition to Fedora... however, the Fedora community has been hit by a broken "update" package which breaks PackageKit. Not a good few days for the testing team over at Redhat.

I've written about it in my blog. See my reaction here:
[URL="http://linuxsoftwareblog.com"]
http://linuxsoftwareblog.com[/URL]

Leace comments on the blog if you wish...

thanks.

---

### Post by K.Mandla on 2008-12-11
Moved to Fedora/Red Hat discussions.

---

### Post by ibutho on 2008-12-11
> **thewOndErEr57 said:**
> Yes,

PackageKit is a great addition to Fedora... however, the Fedora community has been hit by a broken "update" package which breaks PackageKit. Not a good few days for the testing team over at Redhat.

I've written about it in my blog. See my reaction here:
[URL="http://linuxsoftwareblog.com"]
http://linuxsoftwareblog.com[/URL]

Leace comments on the blog if you wish...

thanks.
Every Linux distro (and any OS for that matter) has its ups and downs in terms of QA. A while back Ubuntu was heavily criticised for releasing updates that crippled users systems, openSUSE had similar issues with its package manager etc, so this is not something that is restricted to Fedora. YUM wouldn't update packagekit due to missing dependencies, so nothing was broken. I suspect this was be the same for many users who did not force the update.

---

### Post by igknighted on 2008-12-11
> **ibutho said:**
> As others have mentioned, Fedora has a different philosophy to Ubuntu when it comes to software. Many of their releases are bleeding edge and sometimes include experimental features. Obviously this results in some releases being better than others. Ubuntu is similar in a way, some releases are good and others are bad. 

As for updating, you can use yum to update from one release to another. I have done it myself on a couple of occasions and didn't face any major problems. For the 3D and multimedia stuff, you can install all the required packages from the rpmfusion repository. In Fedora 10, yum seems to have been improved a lot and to me it works just as good as apt, zypper and others.

Yum should not be used to upgrade from version to version.  Anaconda is the traditional tool for this, but with the advent of Fedora 9/10, preupgrade is the method, and it downloads all required packages, then it installs with the system not running so as to avoid as many conflicts as possible.  As mentioned before, the best upgrade method (for any OS), IMHO.

---

