---
title: "new to Ubuntu"
date: 2005-07-18
forum: Desktop Environments
---

### Post by scorpio2002 on 2005-07-18
Hi there!
I've been using Fedora Core for some time and I must admit I'm fed up with it so now I'm looking for other distros. I came here to ask some questions:

1) is ubuntu compatible with .deb pakages? Can I use apt/synaptic with good repos? by good repos I mean reapos where I can find bitorrent, amule, openoffice, xine, nvu etc... constantly updated.

2) does it work fine with Java? (I'm a java programmer)

3) does the installer provide an automatic partitioning mode that takes all the unallocated space, creates the needed partitions and sets grub correctly for a dual-boot system? (yes, I'm still using Windows, after all I can't do without it because of macromedia development software like DreamWeaver and Flash)

4) is it enough stable? I know it's a pretty new release so I wouldn't like to have to cope with millions of bugs.

5) is it well localized in Italian?

Well, that's all :D Thank you all guys! :-)
Donato
Italy

---

### Post by SGC on 2005-07-18
[QUOTE=scorpio2002]
1) is ubuntu compatible with .deb pakages? Can I use apt/synaptic with good repos? by good repos I mean reapos where I can find bitorrent, amule, openoffice, xine, nvu etc... constantly updated.
[/QUOTE]

Yes you can use .deb/apt-get/synaptic since ubuntu based on debian.

For the repositories, you will find them here:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

[QUOTE=scorpio2002]
5) is it well localized in Italian?
[/QUOTE]
For that, you may find [this link](http://www.ubuntuitalia.org/)  helpfull

---

### Post by damonw5 on 2005-07-18
[QUOTE=scorpio2002]Hi there!
I've been using Fedora Core for some time and I must admit I'm fed up with it so now I'm looking for other distros. I came here to ask some questions:

1) is ubuntu compatible with .deb pakages? Can I use apt/synaptic with good repos? by good repos I mean reapos where I can find bitorrent, amule, openoffice, xine, nvu etc... constantly updated.

2) does it work fine with Java? (I'm a java programmer)

3) does the installer provide an automatic partitioning mode that takes all the unallocated space, creates the needed partitions and sets grub correctly for a dual-boot system? (yes, I'm still using Windows, after all I can't do without it because of macromedia development software like DreamWeaver and Flash)

4) is it enough stable? I know it's a pretty new release so I wouldn't like to have to cope with millions of bugs.

5) is it well localized in Italian?

Well, that's all :D Thank you all guys! :-)
Donato
Italy[/QUOTE]
 1) Yes, Ubuntu is compatible with Ubuntu deb packages and somewhat compatible with Debian packages. There are great repos... just enable them by following these directions: [http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)
The universe repos are frozen at release time, but the good folks at Ubuntu Backports keep most of the good ones current :)
It's great! Debian/Ubuntu seems to have a much better packaging system than RedHat/Fedora.

2) I believe you'll find the java packages you need in Ubuntu. You can always preview the packages at [http://packages.ubuntu.com](http://packages.ubuntu.com) ...look at the Hoary release.

3) I'm not sure... But if you know that much about partitions, you can do it yourself using the easy partitioning tool that is part of the installer. Just create one partition that's 2x the size of your RAM for swap, and use the rest for your / partition. Some recommend having a separate partition for /home (I don't).

4) The stable releases are, well, stable. Bugfixes are uploaded to the repositories constantly. The current stable release is 5.04, nicknamed the "Hoary Hedgehog." Like I mentioned, new features are put in the current "testing" release or can be used with the current release by installing the Backports repos. Beware of using the current testing release (nicknamed "Breezy") as many parts of it do not work at the moment.
Ubuntu has a new release every 6 months, so the next one will be in early October. You don't need to reinstall to upgrade, though. You can just use apt or Synaptic to get the newer version by changing a few words in a text file!

5) I don't have firsthand experience, but I believe that Ubuntu has very good international language support.

If you don't want to go for it right away, try out the "live" cd! It will answer many of your questions with no installation! Then if you like it, use the install CD to get a faster, more permanent version :)  [http://ubuntu.com/download](http://ubuntu.com/download)

---

### Post by scorpio2002 on 2005-07-18
Just three more questions and I'll become part of Ubuntu:

6) does it come with the latest version of OpenOffice(I mean, the beta 2)? Even if it's in beta testing, I can't do without OO 2 :-) ;

7) is it possible to talk directly to the developers when there is a problem that seems very difficult to be solved? (as regards as fedora, talking to a developer is impossibile and there are some problems for which you'll never get an answer);

8 ) does it come with all the necessary to watch and listen to mp3s, divxs, DVDs and so on...?
In Fedora, I find pretty annoying the fact that you have to install codecs and good-working players on your own. Today, there is no reason for not including full multimedia support in an operating system.

See you guys, here it's late and I'm going to bed. And again, thank you, you're already making me feel part of the community :D

Ciao from Italy
Donato

---

### Post by damonw5 on 2005-07-18
[QUOTE=scorpio2002]Just three more questions and I'll become part of Ubuntu:

6. does it come with the latest version of OpenOffice(I mean, the beta 2)? Even if it's in beta testing, I can't do without OO 2 :-) ;

7. is it possible to talk directly to the developers when there is a problem that seems very difficult to be solved? (as regards as fedora, talking to a developer is impossibile and there are some problems for which you'll never get an answer);

8. does it come with all the necessary to watch and listen to mp3s, divxs, DVDs and so on...?
In Fedora, I find pretty annoying the fact that you have to install codecs and good-working players on your own. Today, there is no reason for not including full multimedia support in an operating system.

See you guys, here it's late and I'm going to bed. And again, thank you, you're already making me feel part of the community :D

Ciao from Italy
Donato[/QUOTE]
 Hi Donato,

6) In Universe there is version 1.9.79 of OpenOffice.org. To get the latest version, see this thread: [http://ubuntuforums.org/showthread.php?t=30866](http://ubuntuforums.org/showthread.php?t=30866)

7) I've found the developers to be very responsive to users. In addition, there is a HUGE Ubuntu community. If you're having a difficult problem, post it in the Ubuntu Bugzilla: [http://bugzilla.ubuntu.com/](http://bugzilla.ubuntu.com/)

8) It does NOT come with all neccesary codecs. They aren't hard to install, though. Just follow the directions at the great Unofficial Ubuntu Guide here: [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

Ubuntu does not come with everything and everything as does Fedora Core... Therefore it's only one CD, the install is very easy and a broadband connection is recommended. Again, you can try the live CD if you don't want to commit to it right away :)

Ciao from America,
Damon

ARRG! My 8 and a . or ) keep turning into 8)

---

