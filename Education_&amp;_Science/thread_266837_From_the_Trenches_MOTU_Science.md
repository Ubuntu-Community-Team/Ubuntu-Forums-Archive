---
title: "From the Trenches: MOTU Science"
date: 2006-09-27
forum: Education &amp; Science
---

### Post by LaserJock on 2006-09-27
Hi everybody!!
  I'm so glad we finally got our forum! \o/

I thought you might like a little update from the development world. Edgy (6.10) is pretty much frozen for new apps and new upstream (i.e. from the authors) versions but we still have a fair amount of time for bug fixing.

At the last Technical Board meeting the MOTU Science team gained another MOTU which is excellent news, welcome Fujitsu!

I keep a semi-regularly updated list of scientific software at [http://tiber.tauware.de/~laserjock/motuscience/all.html](http://tiber.tauware.de/~laserjock/motuscience/all.html) so people can track Debian and Ubuntu versions. This is mostly for dev us but you might also find it interesting.

Starting to look towards the next release of Ubuntu (Edgy+1) I'd like to get a feel for what the scientific community sees most lacking in Ubuntu. What bugs are the biggest problem? What packages do you want added? etc.

Ground rules:

  1. Keep it to scientific apps. MOTU Science isn't going to turn XGL on by default or anything like that.
  2. If you have an app suggestion please try to also state the license of the program. Most of the time non-free licenses are what keeps things out of Ubuntu.
  3. Just because something is mentioned here doesn't mean it's going to be done right away (if ever really). We have very limited resources (anybody want to help?) so we can only get so much done so it's helpful to prioritize work.

Thanks, rock on!

-LaserJock

---

### Post by Miguel on 2006-09-29
Hi LaserJock,

Do Multiverse apps qualify? Because scilab is still an old version (in dapper at least). I've also had some issues with the fonts. It would be nice to have scilab 4.0 in the repos, and it would be even nicer if it didn't have those weird fonts. Will fill a bug report in malone if needed.

Another issue I have is FORTRAN 95. The available f95 compiler in the official repos is gfortran. However, my codes (check [www.pwscf.org](www.pwscf.org)) only compile with g95 (and IFC of course, which is also faster, but fglrx is enough taint in my system right now). I suppose this compiler thing should be thoroughly discussed. It might be interesting to note that Debian Etch doesn't either supply g95.

*EDIT:* Licences:[list]
[*] g95 is GPL, being a fork of gfortran
[*] Scilab is non-free. The license is available [here](http://www.scilab.org/legal/license.html). According to the FSF:
[quote=The FSF]
**Scilab license:** This is not a free software license because it does not allow commercial distribution of a modified version.
[/quote]
[/list]

---

### Post by akniss on 2006-09-29
How about RKWard?  It aims to be a user-friendly interface for R... which tends to be anything but user friendly when first starting.

[http://rkward.sourceforge.net/](http://rkward.sourceforge.net/)

RKWard is GPL'd.

---

### Post by LaserJock on 2006-09-29
> **Miguel said:**
> Hi LaserJock,

Do Multiverse apps qualify? Because scilab is still an old version (in dapper at least). I've also had some issues with the fonts. It would be nice to have scilab 4.0 in the repos, and it would be even nicer if it didn't have those weird fonts. Will fill a bug report in malone if needed.

Another issue I have is FORTRAN 95. The available f95 compiler in the official repos is gfortran. However, my codes (check [www.pwscf.org](www.pwscf.org)) only compile with g95 (and IFC of course, which is also faster, but fglrx is enough taint in my system right now). I suppose this compiler thing should be thoroughly discussed. It might be interesting to note that Debian Etch doesn't either supply g95.

*EDIT:* Licences:[list]
[*] g95 is GPL, being a fork of gfortran
[*] Scilab is non-free. The license is available [here](http://www.scilab.org/legal/license.html). According to the FSF:

[/list]

Yes, scilab took a lot of effort but we and a new Debian maintainer were able to get scilab4.0 packaged and in for Edgy (6.10). It is enough of a change and difficult to package that I don't think we'll backport it or put it in -updates although if enough people want it I can look into it.

Regarding g95/gfortran, I've had good luck with g95 in OS X on my intel iMac. I hadn't thought of it much in Ubuntu since we have gfortran. Maybe I'll talk to the Debian science guys and see if anybody over there wants to package it. I doubt that MOTU Science really has the resources to maintain a compiler package but I can poke Debian at least ;-)

Thanks for the feedback, keep it coming.

-LaserJock

---

### Post by LaserJock on 2006-09-29
> **akniss said:**
> How about RKWard?  It aims to be a user-friendly interface for R... which tends to be anything but user friendly when first starting.

[http://rkward.sourceforge.net/](http://rkward.sourceforge.net/)

RKWard is GPL'd.

It was included in Ubuntu edgy (6.10) on June 20th.
Launchpad Page: [https://launchpad.net/distros/ubuntu/+source/rkward](https://launchpad.net/distros/ubuntu/+source/rkward)

-LaserJock

---

### Post by Miguel on 2006-10-02
> **LaserJock said:**
> Yes, scilab took a lot of effort but we and a new Debian maintainer were able to get scilab4.0 packaged and in for Edgy (6.10). It is enough of a change and difficult to package that I don't think we'll backport it or put it in -updates although if enough people want it I can look into it.

Oh! I see, thank you very much for your efforts. Rest assured I appreciate it. If you had a little time, and it isn't too off-topic, I'd be interested in hearing the difficulties in packaging scilab. As compiling scilab from source (ver 3.1 at least) was straightforward, I wasn't expecting this.

[QUOTE=LaserJock]Regarding g95/gfortran, I've had good luck with g95 in OS X on my intel iMac. I hadn't thought of it much in Ubuntu since we have gfortran. Maybe I'll talk to the Debian science guys and see if anybody over there wants to package it. I doubt that MOTU Science really has the resources to maintain a compiler package but I can poke Debian at least ;-)
[/QUOTE]

OK, don't worry more than necessary, it's just a wishlist. The binary available in the web works pretty good. Untar somewhere and make some symbolic links in my $PATH. Compiling from source, however, is another problem. Basically because ./configure asks for a gcc file that I don't have.

I could ask for some DFT code, but it simply isn't practical. Because you need every optimization possible for your machine. It's one of the few cases when a few percent points make a difference... except in a small binary where you don't need -O2 or -O3 speed but -O precission.

---

### Post by Miguel on 2006-10-10
Hi LaserJock,

I have a little request regarding gnuplot, but this is probably a "wishlist bug report". The gnuplots of Mandrake 10.0 (my first distro) and Red Hat 3 (the distro in my computing cluster) are version 3.7. These do file autocompletion upon pressing tab. However, gnuplot 4.0 (at least compiled from source by myself, the ones in Ubuntu since 4.10 and the Debian Sarge and Etch ones) do not "tab-complete" names. I don't really know the reason for this. It would be nice to have this feature reactivated.

Thanks in advance,

Miguel

PS: I've recently migrated to Edgy and I just tested scilab 4.0. Great work!!!

---

### Post by LaserJock on 2006-10-10
> **Miguel said:**
> Hi LaserJock,

I have a little request regarding gnuplot, but this is probably a "wishlist bug report". The gnuplots of Mandrake 10.0 (my first distro) and Red Hat 3 (the distro in my computing cluster) are version 3.7. These do file autocompletion upon pressing tab. However, gnuplot 4.0 (at least compiled from source by myself, the ones in Ubuntu since 4.10 and the Debian Sarge and Etch ones) do not "tab-complete" names. I don't really know the reason for this. It would be nice to have this feature reactivated.

Thanks in advance,

Miguel

PS: I've recently migrated to Edgy and I just tested scilab 4.0. Great work!!!

Miguel,
  There is actually a reason for Gnuplot to act that way. Due to some licensing issues, Gnuplot can't be compiled with readline support by default. This is the case in Debian and consequently in Ubuntu. I'm not sure of all the reasoning and why virtually all other distros ship gnuplot with readline support enabled, but I don't think there is anything I can do about it as it is Debian policy. This exact problem was my first introduction to Debian packaging. :-)

-LaserJock

---

### Post by Steveire on 2006-10-10
Can we get the latest version of k3dsurf into the repos?

---

### Post by Miguel on 2006-11-03
Hi again LaserJock,

I have to ask you a favour. Please open scilab, then go to Help->Apropos and browse, using scilab's browser, to any topic. Do you see very ugly fonts? This is not scilab related, though, because I've another program I compiled myself, XCrySDen, and also has these issues on small fonts. The only thing they have in common is use of Tcl-Tk.

I will fill a bug report, but there are so many currently opened it's like crazy.

---

### Post by kleeman on 2006-11-03
Also laserjock scilab 4 cannot install on amd64 because it depends on scilab-bin which in amd64 is still only at the 3 version.

---

### Post by LaserJock on 2006-11-04
Yeah, once I get back from the Ubuntu Developer Summit and get research back in line the MOTU Science team will get cracking on Feisty. Sometimes we get a little overwhelmed with bug reports but I'd much rather have that then broken software that I don't know about. I'm happy to see people submitting bug reports. The more information we get, the better we can get scientific software really rocking for Feisty.

-LaserJock

P.S. also, if people are interested, we can organize some Science Bug Days where anybody can help us squash some bugs.

---

### Post by kleeman on 2006-11-04
Sounds good laserjock. BTW re the scilab problem on amd64, I downloaded the scilab dsc, diff and orig.tar.gz files and compiled the proper scilab-bin version 4 package without issue at all using "fakeroot debian/rules binary". If anyone wants it let me know.

---

### Post by UbuWu on 2006-11-18
I would really like to see [bibus]("http://bibus-biblio.sourceforge.net/") packages for ubuntu.

---

### Post by LaserJock on 2006-11-19
Yeah, I added bibus to our "packages we want" list. I honestly thought it was already in Ubuntu. The bibus website has a debian/ubuntu repo so I think it shouldn't be too hard to get it into universe.

---

### Post by Steveire on 2006-11-19
What about kbibtex from [this repo](http://apsy.gse.uni-magdeburg.de/debian/)? It integrates as a KPart into Kile. There was a release a couple of months ago.
Also is it standard for packages to be updated if there is a more recent version than the edgy one, or should I point those out to you guys so that they get updated? (eg k3dsurf)

Is the 'packages we want list' publically available?

---

### Post by LaserJock on 2006-11-20
> **Steveire said:**
> What about kbibtex from [this repo](http://apsy.gse.uni-magdeburg.de/debian/)? It integrates as a KPart into Kile. There was a release a couple of months ago.
Also is it standard for packages to be updated if there is a more recent version than the edgy one, or should I point those out to you guys so that they get updated? (eg k3dsurf)

Is the 'packages we want list' publically available?

The list is on [http://wiki.ubuntu.com/MOTU/Teams/Science](http://wiki.ubuntu.com/MOTU/Teams/Science) .

Here's a little rundown of how we update the versions in the development release:

1. When the the dev release (feisty in this case) is opened shortly after the previous release (edgy) is released, it starts out as just a copy of the previous release.

2. Packages that Ubuntu hasn't changed in the previous release from Debian get semi-automatically synced over, this process is pretty much done I think for feisty.

3. Packages that **were** changed in Ubuntu have to one-by-one manually examined to see if the Ubuntu changes are still needed. That's called merging.

4. This process continues and new packages are added until the Upstream Version Freeze and Feature Freeze (see [http://wiki.ubuntu.com/FeistyReleaseSchedule)](http://wiki.ubuntu.com/FeistyReleaseSchedule)). After this time new packages and new versions of the upstream (the version we get from the authors) are only allowed by an exception process.

5. After the freezes we focus on bug fixing the packages that we have until the dev release is finally released out to the world.

That's probably way more then what you wanted but it's interesting to see how this is all done.

You can compare the versions of k3dsurf in Debian and Ubuntu by looking at the lists that are on the MOTU Science wiki page. [http://tiber.tauware.de/~laserjock/motuscience/feisty/all.html](http://tiber.tauware.de/~laserjock/motuscience/feisty/all.html) will give you an overview of science packages in Feisty.

-LaserJock

P.S. I added kbibtex to "the list" ;-)

---

### Post by Steveire on 2006-11-20
KTechlab is on the list, but it is in universe already.

I see kbibtex is already in debian unstable. [http://packages.debian.org/unstable/kde/kbibtex](http://packages.debian.org/unstable/kde/kbibtex). As a case study, what can I do to get this package into fiesty universe apart from asking you to take care of it? Can packages like this be put into edgy backports?

Is your page generated automatically?

---

### Post by LaserJock on 2006-11-20
> **Steveire said:**
> KTechlab is on the list, but it is in universe already.

I see kbibtex is already in debian unstable. [http://packages.debian.org/unstable/kde/kbibtex](http://packages.debian.org/unstable/kde/kbibtex). As a case study, what can I do to get this package into fiesty universe apart from asking you to take care of it? Can packages like this be put into edgy backports?

Is your page generated automatically?

Thanks for the KTechlab catch. We picked it up in Edgy.

Well, actually kbibtex was brought into Feisty 6 days ago. At the beginning of the dev release one of the archive admins goes through and finds packages that have been introduced into Debian since our last release and adds them. Unfortunately our backporting policy doesn't allow us to add completely new packages so it won't be in Edgy.

The lists for feisty under "Ubuntu and Debian Packages" on the wiki page are updated daily. The problem is that the misc package list is maintained by hand. It's a human judgment call to decide what is "scientific". I grab the science, math, and electronics sections of the archive automatically, it's only the ones in other sections that I have to add by hand.

-LaserJock

---

### Post by ssam on 2006-12-10
i'd like to see [lybniz]("http://lybniz2.sourceforge.net/") graphing calculator in feisty (though i am biased as i one of the developers.)

i have uploaded it to REVU [http://revu.tauware.de/details.py?upid=3716](http://revu.tauware.de/details.py?upid=3716)

---

### Post by andreag on 2006-12-13
I think that greater support should be given to TeXmacs

[http://www.texmacs.org/](http://www.texmacs.org/)

Actually, a lot of bugs which are easily fixed are left unconfirmed: 

[https://launchpad.net/distros/ubuntu/+bugs?field.searchtext=texmacs&orderby=-importance&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.owner=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://launchpad.net/distros/ubuntu/+bugs?field.searchtext=texmacs&orderby=-importance&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.owner=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

TeXmacs is a new and amazing piece of software, with the potential to become a standard for the production of scientific papers. Among other things, it provides a neat and consistent interface to several mathematical packages, both proprietary, such as Mathematica, Matlab, MuPAD and Maple, and open source, such as Maxima, R, Octave and others. Production-quality graphs may be easily obtained by opening parallel sessions of any of these packages and moving them to the editor window. TeXmacs unites the versatility of Emacs as an interface with external programs with a graphical engine which allows to create complex documents containing LaTeX and PostScript and to render them in real time, without the need for a "preview" window. The combination of these qualities is, I think, unique and truly innovative.

Unfortunately, at least half of the available plugins (for instance those for Mathematica, Maple, Maxima) are broken in Ubuntu Edgy. I think that not only bugs in the distribution should be fixed, but that more visibility should be given to TeXmacs, for instance giving the user the choice to install it as a default editor. At the moment, TeXmacs does not even appear consistently in the Gnome menu (it appears among the Accessories when the right place should be Office) and the texmacs Mime type is not recognized by Gnome, so one can not even open TeXmacs documents by clicking on them (I think there is no such problem instead with KDE, but Ubuntu is mainly Gnome-based and this is a bug that should be fixed).

---

