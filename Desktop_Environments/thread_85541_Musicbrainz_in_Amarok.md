---
title: "Musicbrainz in Amarok"
date: 2005-11-02
forum: Desktop Environments
---

### Post by Psimon on 2005-11-02
I can't get Musicbrainz to work in Amarok. It seems to be running with all the relevent packages installed, but it just says everytime that the track wasn't found. It's not like any of the music is obscure - it MUST be on their database. So I think there must be something I need to configure but I can't find anything.

Any Ideas?

---

### Post by crispingatiesa on 2005-11-03
Yeah, Im having the same issue. Started after the upgrade to Breezy.

---

### Post by metwo on 2005-11-03
You'll need to recompile libtunepimp2c2 in order to get it to work, or you can use mine if you want,

[libtunepimp2c2_0.3.0-2ubuntu8_i386.deb]("http://luc.handsfamily.org.uk/files/ubuntu/libtunepimp2c2_0.3.0-2ubuntu8_i386.deb")

I had to bump the version number up to ubuntu8 to stop apt from wanting to revert to the ubuntu one, which breaks libtunepimp2-dev, so I've got a recompiled one of those too,

[libtunepimp2-dev_0.3.0-2ubuntu8_i386.deb]("http://luc.handsfamily.org.uk/files/ubuntu/libtunepimp2-dev_0.3.0-2ubuntu8_i386.deb")

---

### Post by Psimon on 2005-11-04
[QUOTE=metwo]You'll need to recompile libtunepimp2c2 in order to get it to work, or you can use mine if you want[/QUOTE]

Thank you so much for making those packages available - I wouldn't have a clue how to recompile anything. 

And they work great.

Cheers

---

### Post by cowlip on 2005-11-10
[QUOTE=Psimon]Thank you so much for making those packages available - I wouldn't have a clue how to recompile anything. 

And they work great.

Cheers[/QUOTE]
Thanks too fixed my issue :D (which is 8 months old lol)

---

### Post by mattack on 2005-11-11
This fixed mine too! Thanks!

---

### Post by seezer on 2005-12-08
Didn't work for me (amarok 1.3.7).
The time until 'Couldn't find anything' increased - seems like it's searching.
But doesn't find any titles (i also checked some i did for sure tag with musicbrainz before)..

---

### Post by Prolyprole on 2005-12-12
For Breezy (K/Ubuntu 5.10) you need the debs from the unstable section of Debian rather than testing. You will know if they are the right ones if it is libtunepimp2c2 rather than libtunepimp2.

Go to [http://www.us.debian.org/distrib/packages](http://www.us.debian.org/distrib/packages) and use their package search function. Search for tunepimp in debian unstable. (This is a link to my search results [http://packages.debian.org/cgi-bin/search_packages.pl?keywords=tunepimp&searchon=names&subword=1&version=unstable&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=tunepimp&searchon=names&subword=1&version=unstable&release=all) )

Download these files to an empty folder

libtunepimp-bin
libtunepimp2c2a
libtunepimp2-dev (Install this last one in case you ever want to build amarok from source or try out SVN)

then type: sudo dpkg -i *.deb

If there are no failures in the installation then musicbrainz should hopefully be working for amarok.

To test what formats tunepimp can look up in musicbrainz just type trm from a command line. The last line of the output is the supported files.

Good luck

---

### Post by timtucker on 2006-01-03
[QUOTE=cowlip]Thanks too fixed my issue :D (which is 8 months old lol)[/QUOTE]

Mine too!  Many thanks!

---

### Post by Ninjagecko on 2006-01-04
Thanks so much!

---

### Post by Josef K. on 2006-02-04
since debian packages search site is down (in ages!:evil: ) and I've amd64 I tried to recompile libtunepimp by myself
I downloaded and installed all suggested files (even taglib 1.4) but when I compile libtunepimp it doesn't find libtag... and don't activate the support!... and musicbrainz still doesn't work in amarok

how did you manage to compile libtunepimp?!
:confused:

---

### Post by 7878ponce on 2006-02-07
Thanks metwo for the advice and for hosting your compiled debs, especially whilst the Debian packages site is down.

---

### Post by Gowator on 2006-02-22
[QUOTE=Psimon]Thank you so much for making those packages available - I wouldn't have a clue how to recompile anything. 

And they work great.

Cheers[/QUOTE]
Im just about to try... just downloaded .. if they work or not 

[SIZE="6"]
thank you for taking the time [/SIZE]

edits:

Yuck its still not working ... but wait /etc/debian-version says testing/unstable.  (next try)

---

### Post by Gowator on 2006-02-22
[QUOTE=Gowator]Im just about to try... just downloaded .. if they work or not 

[SIZE="6"]
thank you for taking the time [/SIZE]

edits:

Yuck its still not working ... but wait /etc/debian-version says testing/unstable.  (next try)[/QUOTE]


darn it... 
I tried that and got the wrong version of amarok.. so added the deb testing and unstable to my sources.list ..

This breaks apt ...Ubuntu is configured to stop you doing this it seems to needed to create an apt.conf with a decent cache size 

i.e. 

echo 'APT::Cache-Limit "25165824";' >> /etc/apt/apt.conf

then did an apt-get update and hey... thank goodness apt is no longer broken but then tired installing the amarok using a force-version and it wants to reinstall about half of KDE!!!!  

This is seriously tedious now... fcs I just want musicbrainz lookups from amarok.. why is it so hard????

Anyone help... Im on breezy ... does it work in Dapper?  please help this has been killing me for months!!!!!!!!!!!

---

### Post by metwo on 2006-02-23
[QUOTE=Gowator]This is seriously tedious now... fcs I just want musicbrainz lookups from amarok.. why is it so hard????

Anyone help... Im on breezy ... does it work in Dapper?  please help this has been killing me for months!!!!!!!!!!![/QUOTE]

Have you tried my packages posted above? I think I made them for hoary, but they still seem to work under breezy. If not then try adding this to your sources.list,

```

deb http://archive.czessi.net/ breezy stable stable-updates
deb-src http://archive.czessi.net/ breezy stable stable-updates

```
which should give you 0.3.0-2ubuntu7kubuntu3 as long as you dont have any more recent versions installed.

---

### Post by Gowator on 2006-02-24
Thx,
Yep I did try them and no luck, to many deps during install 

Will try the suggested sources though :D  thanks again.

---

### Post by Gowator on 2006-02-25
Grrr... I am just going in circles with this.  I think I hit the end of the line since I have wasted so much time.  The annoying thing is its not accidental but by design .. (exactly why I will never use Suse because of the Xine hacking to prevent it ever playing css stuff) ...  

I tried the libpimp files as well and tried all I could so I think I might just have to concede a point that Ubuntu is not for me and take advantage of the weekend to backup everything and go back to Debian where I feel more comfortable...  thanks anyway.

---

### Post by Barrakketh on 2006-03-02
[QUOTE=Gowator]Grrr... I am just going in circles with this.  I think I hit the end of the line since I have wasted so much time.  The annoying thing is its not accidental but by design .. (exactly why I will never use Suse because of the Xine hacking to prevent it ever playing css stuff) ...  

I tried the libpimp files as well and tried all I could so I think I might just have to concede a point that Ubuntu is not for me and take advantage of the weekend to backup everything and go back to Debian where I feel more comfortable...  thanks anyway.[/QUOTE]
Hell, it was an easy fix IMO (keep in mind that I already have everything needed to build packages installed, so the packages were built in a dchroot jail), though I do believe it shouldn't be necessary.  Hell, for a little while the amaroK in breezy-backports actually had it working.

This is what I had done to get it working:

[list][*]apt-get source libtunepimpc2c
[*]Delete everything but the libtunepimp-0.3.0 folder.
[*]Edit libtunepimp-0.3.0/debian/control and added an entry for libmad0-dev in Build-Depends, and changed libflac-dev's entry to contain (>=1.1.2-1ubuntu1).
[*]Edited the libtunepimp-0.3.0/debian/changelog file to change the most recent version (0.3.0-2ubuntu7) to 0.3.0-2ubuntu8 so apt-get upgrade wouldn't try reinstalling the version in apt's repository.  I "should" have added a new entry, but I'm lazy).
[*]Remember the control file we opened?  Revisit it and copy the package names out of the Build-Depends section.  You'll need to install those packages for the compile to be successful.  This is the list:
```
debhelper cdbs dh-buildinfo automake1.7 autotools-dev autoconf libtool libid3tag0-dev libogg-dev libvorbis-dev libflac-dev libmusicbrainz4-dev zlib1g-dev libncurses5-dev libreadline4-dev zlib1g-dev doxygen docbook-to-man python2.4-dev python2.3-dev python-dev perl libmad0-dev
```
[*]If you're not already in the libtunepimp-0.3.0 directory, you should switch there now.  Then run 'dpkg-buildpackage -us -uc -rfakeroot'
[*]A bunch of files will appear in the directory above libtunepimp-0.3.0.  You'll want to install libtunepimp2c2_0.3.0-2ubuntu8_i386.deb (which should be the file name if you should get if you made the changes I did).[/list]

---

### Post by metwo on 2006-03-02
The problem is that the libtunepimp deb is compiled without mp3 support due to licencing issues, see

[https://bugzilla.ubuntu.com/show_bug.cgi?id=15708]("https://bugzilla.ubuntu.com/show_bug.cgi?id=15708")

Looks like there will be a multiverse package in dapper to fix this! :)

---

### Post by ruffneck on 2006-04-14
Works like a charm!! Thank you *metwo!*

---

### Post by desheikh on 2006-12-31
Hi,
Just installed libmusicbrainz3-mp3 and you should have musicbrainz working in amarok

---

