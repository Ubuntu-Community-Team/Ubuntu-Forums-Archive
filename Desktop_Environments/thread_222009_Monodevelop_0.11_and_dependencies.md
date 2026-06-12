---
title: "Monodevelop 0.11 and dependencies"
date: 2006-07-24
forum: Desktop Environments
---

### Post by gray-squirrel on 2006-07-24
I noticed for a week that Monodevelop has a new version available.  I was able to attempt an upgrade this past weekend, but I couldn't get anything done.  First, I added this into my [FONT="Courier New"]/etc/apt/sources.list[/FONT]:

```
deb http://debian.meebey.net/ ./
```

which enabled me to download [.deb packages]("http://www.mono-project.com/Downloads#Binaries_for_other_platforms") for Mono and Monodevelop.

I was able to get version 0.10 a few weeks ago this way without incident.

So, with that repository still listed, about a week ago I grabbed an updated list of packages with the usual [FONT="Courier New"]sudo aptitude update[/FONT].  Then, I did the following:

```

squirrel@kubuntu:~ $ sudo aptitude install monodevelop
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  monodevelop
The following packages have been kept back:
  libgecko2.0-cil openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-impress
  openoffice.org-java-common openoffice.org-kde openoffice.org-l10n-en-us openoffice.org-math
  openoffice.org-writer
1 packages upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
Need to get 1573kB of archives. After unpacking 291kB will be used.
The following packages have unmet dependencies:
  monodevelop: Depends: libgecko2.0-cil (>= 0.11-3) but 0.11-1ubuntu3 is installed and it is kept back.
               Depends: libmono-cecil0.4-cil (>= 0.4.1+svn20060703) which is a virtual package.
               Depends: libmono1.0-cil (>= 1.1.13.8) but 1.1.13.6-1pre3 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
monodevelop

Score is 59

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
```

So, to see why [FONT="Courier New"]libgecko2.0-cil[/FONT] is being held back, I did the following:

```

squirrel@kubuntu:~ $ sudo aptitude install libgecko2.0-cil
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libgecko2.0-cil
The following packages have been kept back:
  monodevelop openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-impress openoffice.org-java-common
  openoffice.org-kde openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
1 packages upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
Need to get 30.8kB of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  libgecko2.0-cil: [COLOR="Red"]**Depends: libxul0d but it is not installable**[/COLOR]
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
libgecko2.0-cil [0.11-1ubuntu3 (dapper, now) -> 0.11-1pre0.1 (unstable, unstable)]

Score is -40

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
```

I did a search to see what [FONT="Courier New"]libxul0d[/FONT] was, and it apparently is a part of [FONT="Courier New"]xulrunner[/FONT], by Mozilla.  I downloaded and installed the [[FONT="Courier New"]xulrunner[/FONT] program]("http://www.ubuntuforums.org/showthread.php?t=140811"), but it had no effect - when I tried to upgrade Monodevelop I received the same messages as shown above.  I did a

```
locate libxul0d
```

but got nothing in reply.

Further investigating shows that Debian has [libxul0d]("http://packages.debian.org/unstable/libs/libxul0d"), so I downloaded the package, then attempted to install it to see what would happen, but I got messages about it needing certain dependencies which I'm sure only Debian has.  (It was very early this morning, so I didn't think to copy the output there, but if necessary, I will attempt to install the library again and get the output so I can post it in this thread later this evening.)

Although I may file a bug report later today (depending on how things go), I thought I may make people aware of the situation just in case.  I'm also wondering if anyone has had similar problems attempting to do the same upgrade, and if so, how the dependency issue was resolved.  I'm not sure how [relevant xulrunner is to (K)ubuntu]("http://permalink.gmane.org/gmane.linux.debian.devel.bugs.general/82790"), but the answer to that will be of great help.

Thanks for any advice or any other information you may have.

---

### Post by mlind on 2006-07-24
Those packages are for debian unstable. Ubuntu Dapper doesn't have necessary dependencies for the binaries you're trying to install.

Dapper doesn't have xulrunner (hopefully it's backported though..) and Debian mono libs have been split in ways that didn't happen for Dapper, so you'll get bunch of unresolved dependencies.

You should either download the source package and resolve dependencies (build against libmozilla-dev or backport xulrunner) or find a repository which has newer mono already packaged for Dapper.

---

### Post by gray-squirrel on 2006-07-24
> **mlind said:**
> 
Dapper doesn't have xulrunner (hopefully it's backported though..) and Debian mono libs have been split in ways that didn't happen for Dapper, so you'll get bunch of unresolved dependencies.

You should either download the source package and resolve dependencies (build against libmozilla-dev or backport xulrunner) or find a repository which has newer mono already packaged for Dapper.

Thanks.  I do have backports enabled, but I never saw the [FONT="Courier New"]xulrunner[/FONT] package there, at least not yet.  However, while doing some searching for [FONT="Courier New"]libxul0d[/FONT] a few minutes ago, I did find that it was in the [Edgy repositories]("http://packages.ubuntu.com/edgy/allpackages").  I also see that Monodevelop 0.11 is in the Dapper backports, so I'll comment out the reference to the Debian packages temporarily and see how the upgrade goes.  If the upgrade is not successful, I'll go ahead and file a bug report to see about getting the dependencies backported as well.

---

### Post by mlind on 2006-07-24
> **gray-squirrel said:**
> Thanks.  I do have backports enabled, but I never saw the [FONT="Courier New"]xulrunner[/FONT] package there, at least not yet.  However, while doing some searching for [FONT="Courier New"]libxul0d[/FONT] a few minutes ago, I did find that it was in the [Edgy repositories]("http://packages.ubuntu.com/edgy/allpackages").  I also see that Monodevelop 0.11 is in the Dapper backports, so I'll comment out the reference to the Debian packages temporarily and see how the upgrade goes.  If the upgrade is not successful, I'll go ahead and file a bug report to see about getting the dependencies backported as well.

I don't think backporting of xulrunner will happen though. It (build) depends pretty many other important libraries, which will block the backport. File a bug on backports section though, you never know if actually gets backported.

However, I guess mono backport won't happen for Dapper. It would probably break too many currently working mono applications :(

---

### Post by gmclachl on 2006-08-19
I managed to get Monodevelop 0.11 installed on Dapper by downloading the RPM and then using alien to convert it to a .deb. 

 I had some problems but removing the monodevelop config files seemed to cure it. 

 George

---

