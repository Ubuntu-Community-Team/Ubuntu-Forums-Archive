---
title: "Mangler -- A Ventrilo Client for Linux -- Not releasing Ubuntu binaries"
date: 2011-04-24
forum: Gaming &amp; Leisure
---

### Post by ekilfoil on 2011-04-24
Tonight I've released version 1.2.2 of Mangler.  I will not be creating Ubuntu/Debian binaries for this release.  I am an Ubuntu user as well as a developer and the fact that I have to make this post saddens me.

We have tried getting Mangler into the Ubuntu repos since December 2009.  I now concede defeat.

You can look here for the hoops that we've tried to jump through:  [http://revu.ubuntuwire.com/details.py?upid=7251](http://revu.ubuntuwire.com/details.py?upid=7251)

Going forward, if you want to use Mangler, you will need to use the old version (1.2.1) that we released in Debian package format, the version that playdeb.net provides, or you'll need to compile from source.

Alternatively, the userbase needs to put pressure on Ubuntu to make this package an official part of the Ubuntu repositories.  My apologies to those of you that just want the software to be available.  I simply don't have the time to continue building packages for every available system.

---

### Post by joeelmex on 2011-04-25
I use mangle all the time. I'm now using arch Linux and it works great.  Sorry to hear about your issues in ubunutu.

---

### Post by Tigersmind on 2011-04-25
Thats nuts.

I am running 10.04 and I just checked for Vent software in the Software Center, None.

What reason could it really be to not have this in? Makes no sense.

---

### Post by FrankTheTankC on 2011-04-26
I just compiled it from source.
not too spinebreaking.

---

### Post by polardude1983 on 2011-04-26
I love mangler. and use it a lot :D

That sux though about with Ubuntu though

---

### Post by donkyhotay on 2011-04-26
I've never used mangler myself so maybe I'm missing something but whats wrong with getting it into debian? So long as something is FOSS I've heard it's much easier to get something into debian and from there it gets automatically included in ubuntu. It would also expand the number of distro's your program is included in as well.

---

### Post by Tweak42 on 2011-04-26
Ventrilo is the most popular voip gaming comm but the native client is only windows and mac.  Albeit Mumble and Teamspeak3 are better systems, Mangler is great for those that need to use Ventrilo.  Personally I don't mind compiling for source, but even I can see it would be great for encouragement for new Ubuntu users for Mangler to be included in the Ubuntu Software Center. 

I don't understand the process of getting the software into the repos, where can we go/do to advocate for getting it there?


> **donkyhotay said:**
> I've never used mangler myself so maybe I'm missing something but whats wrong with getting it into debian? So long as something is FOSS I've heard it's much easier to get something into debian and from there it gets automatically included in ubuntu. It would also expand the number of distro's your program is included in as well.

---

### Post by ekilfoil on 2011-04-27
> **donkyhotay said:**
> whats wrong with getting it into debian? So long as something is FOSS I've heard it's much easier to get something into debian and from there it gets automatically included in ubuntu. It would also expand the number of distro's your program is included in as well.

I don't know what the problem is.  Lack of interest from Ubuntu devs seems to the major problem.  Frankly, I've stopped caring.  We're included in both Arch and Gentoo (and have been for a really long time), but I'm no longer willing to work with Ubuntu or Debian until they actually put some effort into working with us.

Considering that this package is used by many thousands of people, you'd think they would actually want to work with us on it.  Unfortunately, that's not the case.

---

### Post by donkyhotay on 2011-04-27
> **ekilfoil said:**
> I don't know what the problem is.  Lack of interest from Ubuntu devs seems to the major problem.  Frankly, I've stopped caring.  We're included in both Arch and Gentoo (and have been for a really long time), but I'm no longer willing to work with Ubuntu or Debian until they actually put some effort into working with us.

Considering that this package is used by many thousands of people, you'd think they would actually want to work with us on it.  Unfortunately, that's not the case.

No, ubuntu gets most of their stuff from debian. If something is included in debian it will (eventually) automatically get into ubuntu. I have only tried packaging/submitting once and it was a headache for me. I heard though that if you submit something to the debian debs (not the ubuntu ones) so long as something is FOSS they are more likely to accept it and once accepted by debian it will get into ubuntu when they take their snapshot of debian that they base ubuntu off of automatically. I've been too busy to work on my personal project recently to worry about getting it accepted by ubuntu or debian but when things settle down for me and I'm ready to dust my project off and get it ready for distribution I plan on going straight to the debian debs, getting it in there, then wait for it to migrate into ubuntu. That way it will be in *both* distro's (and probably much more easily) then trying to get it into ubuntu directly.

---

### Post by Pierrick584 on 2011-04-27
wait wait... why dont you just.... make binary that work on any distro? you know like... only one damn file that everyone could download no matter their linux OS, whats up with insisting on putting deb and rpm package... thats a pure waste of time for devs, and you are just proving how bad it is of a waste of time : \

---

### Post by henz103 on 2011-04-27
> **Pierrick584 said:**
> wait wait... why dont you just.... make binary that work on any distro? you know like... only one damn file that everyone could download no matter their linux OS, whats up with insisting on putting deb and rpm package... thats a pure waste of time for devs, and you are just proving how bad it is of a waste of time : \

+1 yeah portable binary would be great

---

### Post by ekilfoil on 2011-04-28
> **Pierrick584 said:**
> wait wait... why dont you just.... make binary that work on any distro? you know like... only one damn file that everyone could download no matter their linux OS, whats up with insisting on putting deb and rpm package... thats a pure waste of time for devs, and you are just proving how bad it is of a waste of time : \

This is not possible to do.

---

### Post by Iksf on 2011-04-28
A lot of proprietary software for linux has like little installer bash or perl scripts you run, couldn't you do something like that?

---

### Post by Perfect Storm on 2011-04-28
a static binary. A lot of indie games uses it so they don't have to pack to the one zillion distros out there.

---

### Post by donkyhotay on 2011-04-28
> **Artificial Intelligence said:**
> a static binary. A lot of indie games uses it so they don't have to pack to the one zillion distros out there.

The OP is having issues getting the package in the repos. Sure a static binary would work for just distributing on the webpage but hosting your own deb/rpm or even just the source files will work for that. Getting a package in the repos makes it much easier for users to install software.

---

### Post by Perfect Storm on 2011-04-28
> **donkyhotay said:**
> The OP is having issues getting the package in the repos. Sure a static binary would work for just distributing on the webpage but hosting your own deb/rpm or even just the source files will work for that. Getting a package in the repos makes it much easier for users to install software.

I know, but if can't get it into the repositories then there's not much to do, other than binary or setting up a PPA perhaps.

---

### Post by KingHanco on 2011-05-01
I can't get the 1.2.2 to run on Ubuntu 11.04. I'm guesting it won't work at all on Ubuntu 11.04. 1.2.1 will run without any problem.

---

### Post by Bios Element on 2011-05-01
Seems this post is somewhat pointless since the link you provided hasn't had any activity for 4 months. You'd have better chances talking to a MOTU and getting direct feedback to get it packaged.

---

### Post by Tweak42 on 2011-05-02
FYI: [Mangler 1.22]("http://www.ubuntuupdates.org/packages/show/254186") is up on the [GetDeb Games PPA]("http://www.ubuntuupdates.org/ppa/getdeb_games")

---

### Post by RoflHaxBbq on 2011-05-03
This saddens me to see this, even though I use Debian.

It really is simple to compile from source, but that seems to be difficult for some people.

I do have an idea though.

Perhaps somebody could make a script or something that did it for the user.
So when they download the script and execute it, it will wget the source, untar it, then make and make install it.

For Ubuntu it might look a little like:

```

sudo su
wget www.URL.com/source.tar.gz
mkdir SOURCEGOESHERE
tar -options
cd ./SOURCEGOESHERE
make
make install

```

---

### Post by KingHanco on 2011-05-03
Thanks for the links Tweak42.

---

### Post by High Roller on 2011-05-10
Mangler is now in Debian sid.

[http://packages.debian.org/unstable/main/mangler](http://packages.debian.org/unstable/main/mangler)

Here's hoping it trickles down to the 11.10 repos.
I'm not sure when that process would occur.

---

### Post by basotl on 2011-05-10
I just installed via the PPA. Seems to work pretty easily.

---

### Post by High Roller on 2011-05-25
> **High Roller said:**
> Mangler is now in Debian sid.

[http://packages.debian.org/unstable/main/mangler](http://packages.debian.org/unstable/main/mangler)

Here's hoping it trickles down to the 11.10 repos.
I'm not sure when that process would occur.

Looks like Mangler will be included in Ubuntu 11.10:
[https://launchpad.net/ubuntu/oneiric/+package/mangler](https://launchpad.net/ubuntu/oneiric/+package/mangler)

---

