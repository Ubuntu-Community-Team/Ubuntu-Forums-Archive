---
title: "Adobe Acrobat Reader 7"
date: 2005-04-17
forum: Desktop Environments
---

### Post by silent82 on 2005-04-17
Hello!

I've installed Adobe Acrobat Reader in this way:

alien AdobeReader_enu-7.0.0-2.i386.rpm
dpkg -i adobereader-enu*.deb

the installation went OK but when I run
/usr/local/Adobe/Acrobat7.0/bin/acroread
it prints out:
Unable to initialize user interface.

if I load acroread being root all works fine...

any help?

Tanks!

Lorenzo Ferrara

---

### Post by heimo on 2005-04-17
I'd recommend using the Adobe installer (downloading .tar.gz version and running the installer) - I've never had problems installing Acrobat Reader that way.


EDIT: Oh, or you could consider using [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) repository (testing has Acroread 7) - haven't tried it myself. Actually I don't have the .tar.gz version installed either, but had it on Debian Sid.

---

### Post by souki on 2005-04-17
[QUOTE=heimo]EDIT: Oh, or you could consider using [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) repository (testing has Acroread 7) - haven't tried it myself. Actually I don't have the .tar.gz version installed either, but had it on Debian Sid.[/QUOTE]

I can confirm it is worging with debian-marillat testing
I have acoread 7.0-0sarge0.7

---

### Post by ihminen on 2005-04-17
I'm happy to announce that I've got acrobat reader 7 working as well ;-). I think the easiest way to do this is to add the following lines to the /etc/apt/sources.list file:

[FONT=Courier New]
# Acrobat Reader
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
[/FONT]

Then simply update the package list and install the acroread package:

[FONT=Courier New]
sudo apt-get update
sudo apt-get install acroread
[/FONT]

---

### Post by Zakalwe on 2005-04-17
You should give Marillat's repository lower priority so it doesn't overwrite Ubuntu packages.

create the file /etc/apt/preferences and add the following lines.

Package: *
Pin: release o=Christian Marillat
Pin-Priority: 1

To install acrobat reader then just run 

apt-get install acroread=7.0-0sarge0.7

---

### Post by silent82 on 2005-04-17
I've found the problem!!!

I had .adobe and .acrobat directories, in my home, owned by root....

I just did a 
sudo rm -rf .adobe
sudo rm -rf .acrobat

than all worked just fine!

Tank You All!!!!

Lorenzo Ferrara

---

### Post by Psquared on 2005-04-24
When I try to install on Warty I get the message that it cannot install because it needs 

libgtk2.0-0 vers >= 2.6.0 and 2.4.1 is to be installed

libpango1.0-0 vers >= 1.8.1 and 1.6.0 is to be installed.

Can't seem to resolve these dependencies.

---

### Post by moopere on 2005-04-26
[QUOTE=Psquared]When I try to install on Warty I get the message that it cannot install because it needs 

libgtk2.0-0 vers >= 2.6.0 and 2.4.1 is to be installed

libpango1.0-0 vers >= 1.8.1 and 1.6.0 is to be installed.

Can't seem to resolve these dependencies.[/QUOTE]

Download the source code and recompile, or ask jdong (backports project) to do it for you.

Oh?  No source, only a binary blob available?  Well, best not say anymore, lets move on and find something open that works, try kpdf under KDE or evince under gnome - both work and are open source.

I don't mean to be a smart alec here, but honestly, I see folks jumping through unbelieveable hoops trying to get acrobat and realplayer working with limited success most of the time and probably damaging their nicely set up debian based systems in the process.  

If manufacturers like adobe and real as well as a whole bunch of other 'well knowns' out there don't want you to run their software that badly, well, why keep on trying?  Stop begging them for their products, its supposed to be the other way around in a market economy, move on to something that works, works well, and most importantly works well with the operating system you have chosen to run.

I bent over backwards a few months ago when a family member came to visit me for a while and really really really (!!) wanted to view some realplayer streams - its just not worth it.  After ages fubarring around, installing any number of binary blobs and/or crap compiles really meant for redhat I got it working, but then thought....why?   Real streams don't seem any better to me than any other type of stream.  I'd have been better of sending an email to the websites of interest asking them why they are not supporting an opensource streaming media protocol, and in doing so quietly reminding them that if they don't speak my language they can't sell to me.

Anyway, rant off.  

Plenty of excellent programs out their will read pdf's, I've made some suggestions above but there are a heap of others.  Save yourself some time, send adobe an email then enjoy kpdf or eVince.

Cheers,
Craig

---

### Post by morgon on 2005-04-26
Hi!
I have the same problem as pasquared... and it also said:

acroread:
 Depends: libglib2.0-0 but libglib2.4.7-0ubuntu2 is to be installed
 ...
 ...  [-X 

but I already have them installed!!  ](*,) 
 :---) 
Are there any solutions?
 :roll: 

thanks

(evince gives me almost twenty times more complains... :neutral: )

---

### Post by Psquared on 2005-04-26
I'm going to try eVince and installing Acroread using the Adobe binary installer. I'll then post my experience with both.

Just so you will know, I have Warty running on a Pent-M 1.5 with 512 mb ram and a 60 gig harddrive.

It runs like a top right now. Only problem seems to be printing.

---

### Post by ow50 on 2005-04-26
[QUOTE=moopere]Download the source code and recompile[/QUOTE]

In more detail:

Add to /etc/apt/sources.list:
```
deb-src ftp://ftp.nerim.net/debian-marillat/ unstable main
```

```
sudo apt-get update
apt-get source acroread
cd acroread-7.0
fakeroot debian/rules binary
cd ..
sudo dpkg -i acroread_7.0-0.9_i386.deb
```

---

