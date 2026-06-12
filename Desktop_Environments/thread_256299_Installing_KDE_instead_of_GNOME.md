---
title: "Installing KDE instead of GNOME"
date: 2006-09-12
forum: Desktop Environments
---

### Post by cvp on 2006-09-12
I've Googled, and I've searched these forums, but I still just don't get it.
I'm very sorry if this is an obvious answer, but I simply can't figure out how to do this.

I'm using a clean install of Dapper, with the most recent 686 version, and I'm using GNOME.
I want to try out KDE.

I keep seeing **sudo apt-get install kubuntu-desktop**, but I keep getting, "E: Couldn't find package kubuntu-desktop."
I can download plenty of resources for KDE, but not KDE itself.

My /etc/apt/sources.list only has two lines uncommented:
```
deb http://us.archive.ubuntu.com/ubuntu/ dapper dapper-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper dapper-updates main restricted universe multiverse
```

I might as well mention a problem I'm having with apt, because it may very well be related.
When I **sudo apt-get update**:
```
Get:1 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Hit http://us.archive.ubuntu.com dapper Release
Get:2 http://security.ubuntu.com dapper-security Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Fetched 2B in 0s (3B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release  Unable to find expected entry  dapper-updates/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Anyway, can someone pretty please help me?
I just want to try out KDE.

Thanks in advance, and sorry for my ignorance!
-Constantine

---

### Post by TransitMan on 2006-09-12
Put this in your repository list - 
deb [http://kubuntu.org/packages/kde-354](http://kubuntu.org/packages/kde-354) dapper main

Then sudo apt-get reload
sudo apt-get install kubuntu-desktop

---

### Post by TransitMan on 2006-09-12
Also, if you want more offerings from the /etc/apt/sources.list, you need to uncomment about all of them.

As for the problem with the [http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release)  edit this to read "http://archive.unbuntu.com/ubuntu/dists/dapper dapper-updates main restricted universe multiverse" for both deb and deb-src listings.

---

### Post by cvp on 2006-09-12
TransitMan:

Replacing what I have in /etc/apt/sources.list with what you gave me gives horrific results:
```
Err http://archive.unbuntu.com dapper-updates Release.gpg
  Could not resolve 'archive.unbuntu.com'
Ign http://archive.unbuntu.com dapper-updates Release
Ign http://archive.unbuntu.com dapper-updates/main Packages
Ign http://archive.unbuntu.com dapper-updates/restricted Packages
Ign http://archive.unbuntu.com dapper-updates/universe Packages
Ign http://archive.unbuntu.com dapper-updates/multiverse Packages
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Ign http://archive.unbuntu.com dapper-updates/main Sources
Ign http://archive.unbuntu.com dapper-updates/restricted Sources
Hit http://security.ubuntu.com dapper-security Release
Ign http://archive.unbuntu.com dapper-updates/universe Sources
Ign http://archive.unbuntu.com dapper-updates/multiverse Sources
Err http://archive.unbuntu.com dapper-updates/main Packages
  Could not resolve 'archive.unbuntu.com'
Err http://archive.unbuntu.com dapper-updates/restricted Packages
  Could not resolve 'archive.unbuntu.com'
Err http://archive.unbuntu.com dapper-updates/universe Packages
  Could not resolve 'archive.unbuntu.com'
Err http://archive.unbuntu.com dapper-updates/multiverse Packages
  Could not resolve 'archive.unbuntu.com'
Err http://archive.unbuntu.com dapper-updates/main Sources
  Could not resolve 'archive.unbuntu.com'
Err http://archive.unbuntu.com dapper-updates/restricted Sources
  Could not resolve 'archive.unbuntu.com'
Err http://archive.unbuntu.com dapper-updates/universe Sources
  Could not resolve 'archive.unbuntu.com'
Err http://archive.unbuntu.com dapper-updates/multiverse Sources
  Could not resolve 'archive.unbuntu.com'
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Fetched 1B in 0s (1B/s)
Failed to fetch http://archive.unbuntu.com/ubuntu/dists/dapper/dists/dapper-updates/Release.gpg  Could not resolve 'archive.unbuntu.com'
Failed to fetch http://archive.unbuntu.com/ubuntu/dists/dapper/dists/dapper-updates/main/binary-i386/Packages.gz  Could not resolve 'archive.unbuntu.com'
Failed to fetch http://archive.unbuntu.com/ubuntu/dists/dapper/dists/dapper-updates/restricted/binary-i386/Packages.gz  Could not resolve 'archive.unbuntu.com'
Failed to fetch http://archive.unbuntu.com/ubuntu/dists/dapper/dists/dapper-updates/universe/binary-i386/Packages.gz  Could not resolve 'archive.unbuntu.com'
Failed to fetch http://archive.unbuntu.com/ubuntu/dists/dapper/dists/dapper-updates/multiverse/binary-i386/Packages.gz  Could not resolve 'archive.unbuntu.com'
Failed to fetch http://archive.unbuntu.com/ubuntu/dists/dapper/dists/dapper-updates/main/source/Sources.gz  Could not resolve 'archive.unbuntu.com'
Failed to fetch http://archive.unbuntu.com/ubuntu/dists/dapper/dists/dapper-updates/restricted/source/Sources.gz  Could not resolve 'archive.unbuntu.com'
Failed to fetch http://archive.unbuntu.com/ubuntu/dists/dapper/dists/dapper-updates/universe/source/Sources.gz  Could not resolve 'archive.unbuntu.com'
Failed to fetch http://archive.unbuntu.com/ubuntu/dists/dapper/dists/dapper-updates/multiverse/source/Sources.gz  Could not resolve 'archive.unbuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

After adding the kubuntu.org-related deb to sources.list and **sudo apt-get update**-ing, I get a new error message at the end:
```
deb http://kubuntu.org/packages/kde-354 dapper main
```

---

### Post by cvp on 2006-09-13
I really hate to bump this, but I really need an answer.
Is there anyone besides TransitMan who can help me?
It seems like it would be a simple issue regarding my sources.list file, and I can't find the answer anywhere else.

---

### Post by sizzam on 2006-09-13
If you run this from the command line, does it find the kubuntu-desktop package?

```
apt-cache search kubuntu-desktop
```

---

### Post by iovar on 2006-09-13
```
Err http://archive.**unbuntu**.com dapper-updates/restricted Packages
  Could not resolve 'archive.**unbuntu**.com'
Err http://archive.**unbuntu**.com dapper-update
```

```
As for the problem with the http://us.archive.ubuntu.com/ubuntu/...dapper/Release edit this to
read "http://archive.**unbuntu**.com/ubuntu/dists/dapper
dapper-updates main restricted universe multiverse" for both deb and
deb-src listings.
```


Just a  minor typo from TransitMan. It's ubuntu ofcourse.
Change it and try again. It should work.

---

### Post by cvp on 2006-09-13
Okay, I went about fixing it another way, and now it's shiny. But as I am still quite unsure of this, I still have a related question, which I'll put at the end of this post.

**sizzam:**
It didn't. I'm familiar with the **apt-cache search *[app]*** command, and I also looked through the Synaptic Package Manager, and none came up with anything that had "kubuntu" in it, or anything related to KDE that ended with "-desktop."

My brother saw my sources.list file and said, regarding my stacking of the main, dapper, dapper-updates, multiverse, universe, etc., "um... can you *do* that? Try getting a clean sources.list and don't use experimental PERL-inspired nonsense with repository lists ever again."
Anyway, Now that I listed the same repositories with multiple lines, everything works fine, no errors, and I now have access to **kubuntu-desktop**.

So the question that remains is a rather simple one...
When I stripped the first two lines of my sources.list, I ended up with "**deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper**" and the deb-src equivalent, followed by the uncommented additional repositories as provided by the default, unchanged sources.list.
When I tried to **sudo apt-get update**, apt yelled disparaging things about my ancestors and demanded that I change the first line. So after I removed those first two lines, where the only thing listed after the URL is "dapper," things are shiny.

So the question is, do I need "dapper" stuck in there?

---

### Post by cvp on 2006-09-13
**AAAAUUUUUUUUGGGGHHH!!**
Everything not okay! Everything **not** okay!!

Just after making that post you see above, I tried to sudo apt-get install kubuntu-desktop, and I got:

```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: adept but it is not going to be installed
                   Depends: akregator but it is not installable
                   Depends: ark but it is not installable
                   Depends: arts but it is not installable
                   Depends: bogofilter but it is not installable
                   Depends: gtk2-engines-gtk-qt but it is not installable
                   Depends: gwenview but it is not installable
                   Depends: k3b but it is not installable
                   Depends: kaddressbook but it is not installable
                   Depends: kaffeine-xine but it is not installable
                   Depends: kamera but it is not installable
                   Depends: karm but it is not installable
                   Depends: katapult but it is not installable
                   Depends: kaudiocreator but it is not installable
                   Depends: kcontrol but it is not going to be installed
                   Depends: kcron but it is not installable
                   Depends: kde-guidance but it is not going to be installed
                   Depends: kde-systemsettings but it is not installable
                   Depends: kdeadmin-kfile-plugins but it is not installable
                   Depends: kdebase-kio-plugins but it is not going to be installed
                   Depends: kdebluetooth but it is not installable
                   Depends: kdegraphics-kfile-plugins but it is not installable
                   Depends: kdemultimedia-kfile-plugins but it is not installable
                   Depends: kdemultimedia-kio-plugins but it is not installable
                   Depends: kdenetwork-filesharing but it is not going to be installed
                   Depends: kdepim-kio-plugins but it is not installable
                   Depends: kdepim-wizards but it is not installable
                   Depends: kdeprint but it is not going to be installed
                   Depends: keep but it is not installable
                   Depends: kghostview but it is not installable
                   Depends: kicker but it is not going to be installed
                   Depends: kio-apt but it is not installable
                   Depends: kio-locate but it is not installable
                   Depends: klaptopdaemon
                   Depends: kmail but it is not installable
                   Depends: kmailcvt but it is not installable
                   Depends: kmilo but it is not installable
                   Depends: kmix but it is not installable
                   Depends: kmplayer-konq-plugins but it is not installable
                   Depends: knetworkconf but it is not installable
                   Depends: knotes but it is not installable
                   Depends: konq-plugins but it is not installable
                   Depends: konqueror but it is not going to be installed
                   Depends: kontact but it is not installable
                   Depends: konversation but it is not installable
                   Depends: kooka but it is not installable
                   Depends: kopete but it is not going to be installed
                   Depends: korganizer but it is not installable
                   Depends: kpdf but it is not installable
                   Depends: krita but it is not installable
                   Depends: kscd but it is not installable
                   Depends: kscreensaver but it is not installable
                   Depends: ksnapshot but it is not installable
                   Depends: ksplash-engine-moodin but it is not installable
                   Depends: ksvg but it is not installable
                   Depends: ksysguard but it is not going to be installed
                   Depends: ksystemlog but it is not installable
                   Depends: ktorrent but it is not installable
                   Depends: kubuntu-default-settings but it is not going to be installed
                   Depends: kubuntu-konqueror-shortcuts but it is not installable
                   Depends: kwalletmanager but it is not installable
                   Depends: kwin but it is not going to be installed
                   Depends: language-selector-qt but it is not going to be installed
                   Depends: libarts1-akode but it is not installable
                   Depends: libnss-mdns but it is not installable
                   Depends: qca-tls but it is not installable
                   Depends: scim-qtimm but it is not installable
                   Depends: skim but it is not installable
                   Depends: speedcrunch but it is not installable
                   Depends: wlassistant but it is not installable
E: Broken packages
```

It made me shriek in horror and spill my Cheez-Its.

---

### Post by sizzam on 2006-09-13
Here's the contents of my sources.list file.  I haven't manually added any  extra repositories other than multiverse and universe.  Try backing up yours, replace with the contents of mine, then:

sudo apt-get update

Then try installing kubuntu-desktop again.



```


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by cvp on 2006-09-13
All's shiny!

Thank you *soooo* much!

For reference, what was it that made the difference?

---

### Post by TransitMan on 2006-09-13
Glad you got it worked out.

Not sure how your sources.list got corrupted, but since someone else came along and offered their list, it appears you are golden now.

As for the misspelling in your list, ???????????????
Don't remember advising you to change the spelling of anything, except to uncomment. 
But like I said, you got it fixed and are now golden, I hope.

---

### Post by aysiu on 2006-09-14
It's probably too late now, but it's always a good idea, when installing new desktop environments, to use *aptitude* instead of *apt-get*.

More info here:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

