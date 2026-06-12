---
title: "Creating a package"
date: 2009-05-07
forum: General Help
---

### Post by slimx3m on 2009-05-07
i have been trying to create source package and i've been having difficulties.  this is the error message that i get

```
debuild -S
 dpkg-buildpackage -rfakeroot -d -us -uc -S
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package ubbu
dpkg-buildpackage: source version 1.4-1
dpkg-buildpackage: source changed by User <email>
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean
make[1]: Entering directory `/home/irving/ubbu-1.4-2'
make[1]: *** No rule to make target `clean'.  Stop.
make[1]: Leaving directory `/home/irving/ubbu-1.4-2'
make: *** [clean] Error 2
dpkg-buildpackage: failure: fakeroot debian/rules clean gave error exit status 2
debuild: fatal error at line 1329:
dpkg-buildpackage -rfakeroot -d -us -uc -S failed

```

notice i am able to create a *.deb with no problem and i have tried to follow this tutorial ([https://wiki.ubuntu.com/PackagingGuide/Basic](https://wiki.ubuntu.com/PackagingGuide/Basic)) but no success.  any thoughts would be appreciated.

also, just in case is needed i am trying to build a package for a new script that i wrote and then upload it to launchapad.net.

thnx in advance.

---

### Post by mb_webguy on 2009-05-07
There's a class on packaging about to start in about 5 minutes on the #ubuntu-classrom IRC channel, if you're interested.  I have my hands full at the moment, but I'll see if I can find some links for you later if no one else jumps in first.

EDIT:  Sorry, the class begins at 6:00 UTC, which is an hour from now, not in 5 minutes.

---

### Post by slimx3m on 2009-05-07
thnx for the info... that will be 5am my time (CST).  i will see if i could either stay awake or see the last inputs.

do you know by any change if the IRC logs are being saved somewhere?

Edit: oops! wrong time, that would be 1am my time  :)

---

### Post by mb_webguy on 2009-05-07
I don't know if I'll sit through the whole thing, but I'll keep my client open and post the logs somewhere.  It'll be 1:00am local time before the class starts, so I don't know if I'll get it posted tonight.  If I don't, I'll get it up as soon as I can tomorrow and post a link to it here.

EDIT:  I just noticed you said 5am CST...  We're in the same time zone.  6:00 UTC is 1:00 CST.  You can use the command "date -u" in the terminal to view the current UTC time.

---

### Post by slimx3m on 2009-05-07
yes, i got it wrong :P, it is 1am and not 5am. :)

---

### Post by mb_webguy on 2009-05-07
Ok...  here's the log from [kirkland's #ubuntu-classroom discussion on packaging (6:00 UTC, 07-05-2009)]("http://irclogs.ubuntu.com/2009/05/07/%23ubuntu-classroom.html").  He focused primarily on how to make packages and distribute them through a Launchpad PPA, with emphasis on the latter.  I thought he'd discuss the actual packaging process more, but it's still pretty interesting.  If you're building your own packages, a PPA is certainly something to think about.

I'm heading for bed now, but I'll see if I can round up some links on packaging tomorrow.

---

### Post by Alterax on 2009-05-07
In the meantime, here's the link for the Debian New Maintainer's Guide.  I learned how to make packages from it, and it's pretty much identical to the process I use for Ubuntu packages.

[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)

If you have any trouble, shoot a message over to me.  I usually check in on and off during the day, and it's still pretty fresh on my mind.

Oh, and what it looks like is in your Makefile, there isn't an option for 'clean'.  The clean section of it just tells the make tools to delete the target files.  That way if you've built it before but made some alterations to your code since, you won't accidentally end up with old binaries.  Typically the dpkg-buildpkg scripts invoke 'make clean' first; if it fails on this point, then it borks the whole thing.

Quick fix:  Add a line to the end of your Makefile that just says:
```
clean:
```
Ideally, you want to put in that section the commands to delete the file it has generated, but if you're just wanting to chuck something into a .deb package, it's not really a big deal

---

### Post by slimx3m on 2009-05-07
if you could help me that would be great.  i am currently having difficulties trying to connect to my PPA, I really don't know what I am doing wrong.

i feel dumb....... :(

---

### Post by Alterax on 2009-05-07
Well, I don't do "I feel dumb..." You can't really blame yourself for not knowing how to do what you've never done before, am I right?

Can you make a gzipped tarball of the program you're working on and send it to me?  It always helps to have the code handy.

---

### Post by slimx3m on 2009-05-07
yes... the thing is that even though this is my first time doing this i always find my day out and i figure it out. but this time....... i guess is a not. :(.

oh well... really thnx for your help.

---

### Post by slimx3m on 2009-05-07
alright, i got it figured out... thnx to the help of Alterex (forums) and directhex (IRC #ubuntu-motu)

in the current directory i needed to add this file called "Makefile"
```
clean:

install:
    /bin/bash ubbu
```
then had to replace my rules under "$CURRENT-DIRECTORY/debian/rules" with the following

```

#!/usr/bin/make -f
%:
	dh $@

install:
	dh install --before dh_auto_install
	$(MAKE) DESTDIR=$(CURDIR)/debian/tmp/ubbu install
	dh install --after dh_auto_install

```

then had to run this command
```
dpkg-buildpackage -S -sa -rfakeroot
```

and it worked perfectly!!!

thnx for your help guys!!!

---

