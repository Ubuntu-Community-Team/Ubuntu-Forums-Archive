---
title: "GnuCash 2.0"
date: 2006-07-10
forum: Desktop Environments
---

### Post by apastuszak on 2006-07-10
So, I know it's only been a couple of hours, but has anyone rolled this into a .deb yet?  I think that having a personal financial app that can download transactions directly from a bank is a huge plus for Desktop Linux.

---

### Post by beameup on 2006-07-10
Gnucash can do that now? I'll have to do some reading.
OK, I did!
> Major changes in the milestone release include;

    * OFX DirectConnect which can directly retrieve and import account statements over the Internet.
    * A "Hide account" feature to keep a better overview of your current accounts tabbed window functionality.
    * The ability to create budgets within GnuCash using your account data.
    * Support for Accounting Periods.
    * The data file format has been improved with respect to international characters. Data files with international characters can be transferred to other countries flawlessly.
    * GnuCash Help and Guide are now fully integrated with the GNOME Help system (Yelp).

Source: [http://www.gnucash.org/](http://www.gnucash.org/)

---

### Post by vbatts on 2006-07-10
i haven't found an "official" release of, just the RC pre-release for Dapper.
you can read about the RC for edgy on ubuntus forums.

the Dapper RC candidate i found 
[http://www.math.nyu.edu/faculty/kleeman/dapper/](http://www.math.nyu.edu/faculty/kleeman/dapper/)
(obviously, its the gnucash 1.9.8)

---

### Post by vbatts on 2006-07-10
damn the smiley
1.9.8

---

### Post by mazirian on 2006-07-10
You'll find Kleemen's debs for 2.0 here.  They work well after you sort out the dependancies.  [http://ubuntuforums.org/showthread.php?t=127587&page=10&highlight=gnucash](http://ubuntuforums.org/showthread.php?t=127587&page=10&highlight=gnucash)

---

### Post by kleeman on 2006-07-10
For Ubuntu dapper:

»[www.yourfilelink.com/get.php?fid=133573](www.yourfilelink.com/get.php?fid=133573)

»[www.yourfilelink.com/get.php?fid=133506](www.yourfilelink.com/get.php?fid=133506)

First is the software and the second the documentation.

---

### Post by apastuszak on 2006-07-10
That truly was quick.  I installed the debs and then ran gnucash & from the command line, since nothing gets added to the applications menu, and gnucash threw a bunch of errors.

I wish I had written down what the failed dependencies were, but I just basically did a search in Synaptic for everything the terminal window told me I was missing and in the end Gnucash fired up.

Now once it actually loads it throws error saying it needs libofx and I think lilbaqbaking.  I added those and relaunched and it worked like a charm.

Off to try out online banking...

Andy

---

### Post by honeydew on 2006-07-10
andy Im in the same boat as you, Im going to try nd install from source this evening.. if all goes well.. Ill post a cheap howto.

---

### Post by Lfrb on 2006-07-11
> gnucash-bin: error while loading shared libraries: libgsf-gnome-1.so.113: cannot open shared object file: No such file or directory


somebody knows what that means ??

---

### Post by boobytrapped on 2006-07-11
> **Lfrb said:**
> somebody knows what that means ??

The gnucash package seems to be not constructed properly with all the dependencies defined.  This error message is complaining about a library missing.  I was able to get around these problems by installing the following packages
```

sudo apt-get install slib guile-1.6-slib libltdl3 libgwrapguile1 libgsf-gnome-1-113
```

---

### Post by justinjstark on 2006-07-11
It's pretty.  But definitely still not as pretty as Grisbi Finance Manager.

Thanks for the .debs.

---

### Post by dolson on 2006-07-11
I [personally] wouldn't use a .deb that was made with checkinstall, which I am assuming this was, since it doesn't handle any dependencies whatsoever and can cause conflicts with files in other packages [resulting in big a mess when you try to uninstall one, if you have force-installed].

There is section in Dapper's help system about packaging properly, and it's not too hard once you get into it, but it isn't as easy as the quick and dirty checkinstall. It took me a few years before I decided to venture into packaging without checkinstall because I thought it would be hard. :)

Anyhow, here are the steps I followed to rebuild Debian's GnuCash 2.0.0 debs on Dapper:

Add the Debian source line to /etc/apt/sources.list, so that we can download the source packages easily. This won't interfere in any way with Dapper's sources, aside from source packages, which most people don't use. If in doubt, you can simply comment it or remove it after you are done with this how-to.

```
deb-src http://ftp.debian.org/debian/ unstable main contrib non-free
```


Add the key for the Debian mirror:

```
gpg --recv-key 010908312D230C5F
gpg --armor --export 010908312D230C5F | sudo apt-key add -
```

Ok, we need to install the dependencies to build GnuCash. There are a lot, but you can remove them after the build if you want to, it's really not going to harm anything, other than taking up disk space though.

```
sudo aptitude update
sudo aptitude install devscripts libltdl3-dev libofx-dev ofx libfinance-quote-perl guile-1.6-slib guile-1.6-dev m4 gettext libdb3-dev slib debhelper zlib1g-dev libjpeg62-dev liborbit-dev libungif4-dev libxml-parser-perl x11-common libglib2.0-dev libxml2-dev libbonobo2-dev libgnomevfs2-dev libgnomevfs2-extra libgtk2.0-dev libglade2-dev libgnomeprint2.2-dev libart-2.0-dev libgconf2-dev libgnomeui-dev libgsf-gnome-1-dev libpango1.0-dev libgtkhtml3.8-dev gconf2 g-wrap build-essential
```

That should be all. Now, let's download the source and modify the rules file to enable online banking:
```
cd /tmp/
apt-get source gnucash
cd gnucash-2.0.0/
gedit debian/rules
```

Find the line in this file that says:
> env LDFLAGS="-L/usr/X11R6/lib" GUILE=/usr/bin/guile-1.6 CFLAGS="$(CFLAGS)" ./configure --disable-static --sysconfdir=/etc --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --libexecdir=/usr/lib --libdir=/usr/lib/gnucash --enable-ofx --disable-error-on-warning  || cat config.log
and change it to say:
> env LDFLAGS="-L/usr/X11R6/lib" GUILE=/usr/bin/guile-1.6 CFLAGS="$(CFLAGS)" ./configure --disable-static --sysconfdir=/etc --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --libexecdir=/usr/lib --libdir=/usr/lib/gnucash --enable-ofx --enable-hbci --disable-error-on-warning  || cat config.log

This should be on line 24. The only change is to add in [color=red]--enable-hbci[/color] to the line. Save the file and close Gedit. Now try checking the dependencies:
```
debuild -us -uc
```

This should complain about python2.3 (unless you have it installed), and nothing else. If there is another missing dependency, install it. But if it says only python2.3, then you're good to go. Run this:

```
debuild -d -us -uc
```

We use the -d parameter to override the python2.3 requirement, as Ubuntu ships with 2.4 by default, and there's really no need to install another python. Alternately, you could edit the debian/control file to specify python2.4, but this works too.

Anyhow, once it's done building, you can install the dependencies and the resulting [slightly more properly packaged] .debs:

```
sudo aptitude install libdate-manip-perl psfontmgr guile-g-wrap libaqbanking0c2a libffi4 libgsf-gnome-1-113 libgwrap-runtime0 libktoblzcheck1c2a libofx2c2a slib guile-1.6-slib libfinance-quote-perl
sudo dpkg -i ../*.deb
```

There are almost certainly missing dependencies that should be added to debian/control because we have modified the original debian package to include the HBCI support...

You can do this with many packages, and it's a good way to learn a bit about packaging if you try to do this with a package that needs slight changes to build on Ubuntu.

Thanks to kleeman and desp for work on this as well.

[[My .deb packages]](http://ubuntustudio.com/uploads/dapper/gnucash-2.0.0/)

---

### Post by ansorg on 2006-07-11
> **dolson said:**
> ...
You can do this with many packages, and it's a good way to learn a bit about packaging if you try to do this with a package that needs slight changes to build on Ubuntu.

[[My .deb packages]](http://ubuntustudio.com/uploads/dapper/gnucash-2.0.0/)

thanks, great explanation

Do you have any idea whether installing (building) GnuCash2 in this way would work on a x86_64 system?


thanks

---

### Post by dolson on 2006-07-11
It definitely should work because it's basically how all the packages are generated for distros like Ubuntu and Debian (maybe they use pbuilder, but that is beyond the scope of this how-to, since it's a bit more involved and isn't necessary for end-users who just want to build a few packages for themselves to use - it's more for people building new packages from scratch). I only have 32-bit Ubuntu on my system here at work right now, so I can't build it.

---

### Post by kleeman on 2006-07-11
> **dolson said:**
> I wouldn't use a .deb that was made with checkinstall, which I am assuming this was, since it doesn't handle dependencies.
[[My .deb packages]](http://ubuntustudio.com/uploads/dapper/gnucash-2.0.0/)

You are right the packages were built with checkinstall and I agree this is suboptimal. I was doing it this way to track the 1.9 development release since the packages could be installed side by side with the stable version from dapper. Thanks for your debs. Hopefully this will work it's way into backports shortly.

By the way it might be nice if you could recompile your debs with ofx and hbci support so that the online banking is enabled as many people have asked about this in the other thread...

---

### Post by dolson on 2006-07-11
Since you seem to know more about GnuCash, can you tell me what I have to change? I know how to package, but I don't use GnuCash.

This looks to me like it is using OFX:

checking whether to use OFX... yes -- failure is fatal
checking for libofx version >= 0.7.0... found 0.8.0
checking for libofx/libofx.h... yes
checking for libofx... yes

I looked in the other thread and don't see configure flags or anything like that. I did install another library and will recompile to see if it's any different, but I am not expecting it to. These are the official debian packages, so it's strange they wouldn't have this enabled by default.

---

### Post by kleeman on 2006-07-11
> **dolson said:**
> Since you seem to know more about GnuCash, can you tell me what I have to change? I know how to package, but I don't use GnuCash.

This looks to me like it is using OFX:

checking whether to use OFX... yes -- failure is fatal
checking for libofx version >= 0.7.0... found 0.8.0
checking for libofx/libofx.h... yes
checking for libofx... yes

I looked in the other thread and don't see configure flags or anything like that. I did install another library and will recompile to see if it's any different, but I am not expecting it to. These are the official debian packages, so it's strange they wouldn't have this enabled by default.

I used the following:

./configure --enable-ofx --enable-hbci --disable-error-on-warning

Note that you need the aqbanking packages including the dev ones installed. 
To find them search for "aqbank" in synaptic.

---

### Post by honeydew on 2006-07-11
Im getting this error after I compiled the deb. and Im trying to install.. when making the I got some gpg errors.. anyone think that this error might be related?

```

sudo dpkg -i gnucash_2.0.0-1_i386.deb
Password:
Selecting previously deselected package gnucash.
(Reading database ... 89974 files and directories currently installed.)
Unpacking gnucash (from gnucash_2.0.0-1_i386.deb) ...
dpkg: dependency problems prevent configuration of gnucash:
 gnucash depends on gnucash-common (>= 2.0.0-1); however:
  Package gnucash-common is not installed.
dpkg: error processing gnucash (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnucash

```

---

### Post by dolson on 2006-07-11
You need to install both .deb packages that are generated.

---

### Post by honeydew on 2006-07-11
now, how would we incorporate the OFX into the creation of this deb? I dont know much about this software, only thing I know is I need to start keeping track of my money :KS  so full featured software is nice :D

---

### Post by dpm on 2006-07-11
> **dolson said:**
> 
Add the Debian source line to /etc/apt/sources.list, so that we can download the source packages easily. This won't interfere in any way with Dapper's sources, aside from source packages, which most people don't use. If in doubt, you can simply comment it or remove it after you are done with this how-to.

```
deb-src http://ftp.debian.org/debian/ unstable main contrib non-free
```

After adding this line to my /etc/apt/sources.list and running either

```
sudo apt-get update
``` 
or

```
sudo aptitude update
``` 
I got the following error:

```
W: GPG error: http://ftp.debian.org unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F
``` 
which I solved by executing the following commands:

```
gpg --recv-key 010908312D230C5F
gpg --armor --export 010908312D230C5F | sudo apt-key add -
```

---

### Post by honeydew on 2006-07-11
your directions worked wonders by the way.. at this point I only need one extra pair of hands to count my funds..($30) but I am on my way to millions! 


thankyas!

---

### Post by etank on 2006-07-11
I keep getting the following:```
gpg: requesting key 2D230C5F from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

```
What am I doing wrong?

---

### Post by dpm on 2006-07-11
> **dolson said:**
> I looked in the other thread and don't see configure flags or anything like that. I did install another library and will recompile to see if it's any different, but I am not expecting it to. These are the official debian packages, so it's strange they wouldn't have this enabled by default.

HBCI support is not enabled in the official Debian packages because of licensing issues with openssl, which aqbanking, the library providing this functionality indirectly uses. So we won't be seeing an HBCI enabled GnuCash in Debian unless openssl changes its license or aqbanking starts using gnutls as a replacement for openssl, for example. Neither of these two situations are very likely to happen in the near future, AFAIK. So people who are using HBCI will always have to resort to adding --enable-hbci to debian/rules and rebuilding the package from the Debian sources. HBCI is widely used in Germany by most banking institutions.

OFX, on the other hand, is enabled by default in the official Debian package.

---

### Post by dpm on 2006-07-11
> **etank said:**
> I keep getting the following:```
gpg: requesting key 2D230C5F from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

``` What am I doing wrong?

My guess is that you mistyped the command, as gpg is requesting only part of the key. Try to type this again:
[FONT=monospace]
[/FONT]```
gpg --recv-key 010908312D230C5F
``` 
Does that work?

---

### Post by dolson on 2006-07-11
I updated the instructions in my previous post to allow online banking. It should be right now, and it's really quite easy to enable. Thanks to kleeman for the fix.

[HOW-TO link](http://ubuntuforums.org/showpost.php?p=1241048&postcount=12)

I may have missed some dependencies.. And since we're venturing beyond debian's official package here, we ideally should update the debian/control file to reflect the dependencies. But.. I'm lazy and should be working right now. ;)

---

### Post by dpm on 2006-07-11
> **dolson said:**
> Run this:
```
debuild -d
``` 

Running this results in the following error:
```
gpg: skipped "Thomas Bushnell, BSG <tb@debian.org>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available
``` 
so I guess it might be better to run debuild without checking the package's signature:
```
debuild -d -us -uc
```

---

### Post by xlyz on 2006-07-11
I'm lost. how can I install it? (don't care about HBCI)

---

### Post by dolson on 2006-07-11
> **desp said:**
> After adding this line to my /etc/apt/sources.list and running either

```
sudo apt-get update
``` 
or

```
sudo aptitude update
``` 
I got the following error:

```
W: GPG error: http://ftp.debian.org unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 010908312D230C5F
``` 
which I solved by executing the following commands:

```
gpg --recv-key 010908312D230C5F
gpg --armor --export 010908312D230C5F | sudo apt-key add -
```

Yeah, you're right. But I just ignore those errors, since the source is still made available. But I added your tip to my post anyway.

> **desp said:**
> Running this results in the following error:
```
gpg: skipped "Thomas Bushnell, BSG <tb@debian.org>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available
``` 
so I guess it might be better to run debuild without checking the package's signature:
```
debuild -d -us -uc
```

True. It does build the packages anyhow, so I just left those switches out, but I have updated the howto anyway. :)

> **xlyz said:**
> I'm lost. how can I install it? (don't care about HBCI)

Just follow the howto on page 2, post 12. [HOW-TO link](http://ubuntuforums.org/showpost.php?p=1241048&postcount=12)

---

### Post by xlyz on 2006-07-11
I was looking for binaries ;)

---

### Post by dpm on 2006-07-11
> **xlyz said:**
> I was looking for binaries ;)

If you had bothered reading the thread you would have found the binaries.

---

### Post by kleeman on 2006-07-11
> **dolson said:**
> I updated the instructions in my previous post to allow online banking. It should be right now, and it's really quite easy to enable. Thanks to kleeman for the fix.

[HOW-TO link](http://ubuntuforums.org/showpost.php?p=1241048&postcount=12)

I may have missed some dependencies.. And since we're venturing beyond debian's official package here, we ideally should update the debian/control file to reflect the dependencies. But.. I'm lazy and should be working right now. ;)

Cool dolson online banking works well now with standard packages :) . One final gotcha from the other thread you might want to put in the howto:

There is a bug in the aqofxconnect-qt3-wizard program in the libaqbanking-ofx0 package meaning a library is misplaced. To fix do the following

cd /usr/lib

sudo ln -s /usr/lib/aqbanking/plugins/0/providers/aqofxconnect.so.1.0.1 libaqofxconnect.so.0

And to be a further PITA you may wish to produce an updated documentation deb as well. The package I produced with checkinstall only works with my checkinstall gnucash-2.0 deb. The developers have done a fair bit of work updating this and it is really very helpful.

---

### Post by JSVH on 2006-07-11
What do people think of it? does online banking work? Does it work as good as Quicken? When do can we expect a ubuntu ready 2.0.0 in the regular repositories?

---

### Post by dolson on 2006-07-11
It will hit Edgy whenever they do the merge and syncs from Debian Sid.

I have added some dependencies to the list that I found when I tried to install at home. I could just check the list, but whatever. heh. Or you can install the packages with gdebi, which installs dependencies.

I haven't run into any issues that requires making any symlinks. How do you access this bug from within GnuCash? I can start the HBCI Wizard and go through to where it launches the [ugly] QT-based wizard and asks me about keys or pins or whatever, but I don't know any info to fill in there.

Also, when I checked, the deb for gnucash-doc was not updated to 2.0.0 yet on the Debian servers.

---

### Post by beameup on 2006-07-11
> **JSVH said:**
> What do people think of it? does online banking work? Does it work as good as Quicken? When do can we expect a ubuntu ready 2.0.0 in the regular repositories?
I'll withold my judgement until it's humming along.
 I currently use Moneydance and it has been said it's as good or better than Quicken. I came from MS Money(that wants everything stored on their servers and you have to do the passport thing) so I can't compare. I'm happy with Moneydance. It's a commercial app.

---

### Post by drfox on 2006-07-12
Great instructions, dolson. Everything is up and running. I found OFX under HCBI setup.

Quick question. When I tried to run debuild, I got a "command not found" error. Do I need to fix something in Dapper?

Thanks a lot. Larry

---

### Post by dolson on 2006-07-12
Ah! It is in the devscripts package. :)

---

### Post by mazirian on 2006-07-12
Thanks dolson!  That worked quite well.  FWIW, I had to add in the development packages for libssl and libaqbank to get it to compile with the hbci support.

---

### Post by kleeman on 2006-07-12
> **dolson said:**
> It will hit Edgy whenever they do the merge and syncs from Debian Sid.

I have added some dependencies to the list that I found when I tried to install at home. I could just check the list, but whatever. heh. Or you can install the packages with gdebi, which installs dependencies.

I haven't run into any issues that requires making any symlinks. How do you access this bug from within GnuCash? I can start the HBCI Wizard and go through to where it launches the [ugly] QT-based wizard and asks me about keys or pins or whatever, but I don't know any info to fill in there.

Also, when I checked, the deb for gnucash-doc was not updated to 2.0.0 yet on the Debian servers.
There are two wizards. Go to Tools ----> HBCI Setup then on the second page press Start AqHBCI Wizard. This then gives two options (aqofxconnect -US banks and aqhbci --German banks) select the first radio button
 and click Configure. This launches the following program:

/usr/lib/aqbanking/plugins/0/wizards/aqofxconnect/aqofxconnect-qt3-wizard

and this on my system crashes with a missing library.

As an interim solution on the documentation here is a checkinstall deb with the correct directory structure to work with your debs.

 [http://www.yourfilelink.com/get.php?fid=134626](http://www.yourfilelink.com/get.php?fid=134626)

---

### Post by Bad2theBone on 2006-07-14
On folowing Dolson's HowTo I'll get the folowing error on debuild:

# dh_testroot
dh_clean -k
dh_installdirs
make
make[1]: Entering directory `/tmp/gnucash-2.0.0'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/tmp/gnucash-2.0.0'
make: *** [build-stamp] Error 2
debuild: fatal error at line 768:
dpkg-buildpackage failed!

I'm totally clueless what this is trying to tell me.](*,) 

TIA

---

### Post by nicbink on 2006-07-16
> **Bad2theBone said:**
> On folowing Dolson's HowTo I'll get the folowing error on debuild:

# dh_testroot
dh_clean -k
dh_installdirs
make
make[1]: Entering directory `/tmp/gnucash-2.0.0'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/tmp/gnucash-2.0.0'
make: *** [build-stamp] Error 2
debuild: fatal error at line 768:
dpkg-buildpackage failed!

I'm totally clueless what this is trying to tell me.](*,) 

TIA


were you able to resolve this?

---

### Post by Bad2theBone on 2006-07-17
Yes & No.

Yes, I've got GnuCash 2.0 working on my system, but no I was not able to create the .deb pkg. I wound up manually going through the steps of installing from source. (./configure, make, make install, & make clean).

I would still like to find out what this error is so that I could create a pkg.

---

### Post by dangral on 2006-07-17
I am getting the same error message when running ```
debuild -d -us -uc 
```

---

### Post by Apreche on 2006-07-17
I am also getting the same error.

---

### Post by nicbink on 2006-07-17
> **Bad2theBone said:**
> I wound up manually going through the steps of installing from source. (./configure, make, make install, & make clean).

I would still like to find out what this error is so that I could create a pkg.


i ended up installing the provided debs previously posted in the forums.  though at first it was giving me a guile error when launching.  i checked the dependencies (all were installed) so I had synaptic reinstall/reconfigure them and it worked.

---

### Post by VirtuAlex on 2006-07-18
I compiled my from source for amd64. "Get quotes" button in the price editor is grayed out. I installed Finance::Quote through perl cpan, it did not help. What can be wrong?

---

### Post by tuxcantfly on 2006-07-18
how about you just do the usual ./configure and make but use checkinstall (sudo checkinstall make install)? it also can create deb packages

---

### Post by dolson on 2006-07-19
"Deb packages" yes, "proper Deb pacakges with dependency info and so forth" no.

---

### Post by dobbs on 2006-07-20
> **nicbink said:**
> i ended up installing the provided debs previously posted in the forums.  though at first it was giving me a guile error when launching.  i checked the dependencies (all were installed) so I had synaptic reinstall/reconfigure them and it worked.

I'm new to Ubuntu (I am very impressed so far!) having used various Linux distributions in the past. I was able to muddle through and get GnuCash installed and running. The only thing I don't seem to have installed properly is the tutorial and help files. I used the .deb packages in this thread and modified my launcher to /usr/bin/gnucash. Anyone know where the tutorial might be hiding? :confused:

---

### Post by dobbs on 2006-07-20
Okay, I figured it out. I think I had downloaded an earlier verion of the documentation. Using the current .deb did the trick.

Ubuntu is a major accomplishment. My hat is off to the developers. I've already got this machine printing to the all-in-one machine being shared by my Windows machine, I've installed and updated a dozen or so useful applications, including GnuCash - which happened to be my primary reason for giving Ubuntu a whirl. I've been creaking along with QuickBooks for years, with my dying Windows 2000 desktop crashing at least once every couple of days. In one afternoon I've given another clunker PC a new lease on life. I am stunned at how clean and functional this is!

---

### Post by mazirian on 2006-08-12
Anyone built the new release yet?  Any troubles with it?

---

### Post by kleeman on 2006-08-12
Yeah I have. See this thread for debs:
[http://www.ubuntuforums.org/showthread.php?t=222221&page=2](http://www.ubuntuforums.org/showthread.php?t=222221&page=2)
Seems faster and more stable

---

### Post by goodmorningeuclid on 2006-11-13
> **Bad2theBone said:**
> On folowing Dolson's HowTo I'll get the folowing error on debuild:

# dh_testroot
dh_clean -k
dh_installdirs
make
make[1]: Entering directory `/tmp/gnucash-2.0.0'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/tmp/gnucash-2.0.0'
make: *** [build-stamp] Error 2
debuild: fatal error at line 768:
dpkg-buildpackage failed!

I'm totally clueless what this is trying to tell me.](*,) 

TIA


I encountered the same fatal error (line 768) when building gnu-cash-2.0.2. Eventually I determined that I was missing the aqbanking-dev libraries.

```
sudo apt-get install libaqbanking0-dev
```

After that the build went smoothly.

---

