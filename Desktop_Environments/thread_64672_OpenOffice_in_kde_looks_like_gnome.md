---
title: "OpenOffice in kde looks like gnome"
date: 2005-09-11
forum: Desktop Environments
---

### Post by yhotg on 2005-09-11
how can i change the look & feel of OOo in kde?
i tweeked into the OOo options,
and qt

any idea?

and by the way, is there any openoffice1.1.4 .deb for hoary?

---

### Post by yoloosis on 2005-09-11
OOo seems to be programmed with gtk, so I don't think is possible to make it look like a KDE application...

---

### Post by treris on 2005-09-12
Have you installed the openoffice.org(2)-kde package from the repositories, there's one for both 1.1.3 and the 2.0 beta version of OOo. This should help somewhat in making OOo look more at home in KDE

As far as I know there is no 1.1.4 deb-package for (k)ubuntu

---

### Post by yhotg on 2005-09-12
[QUOTE=treris]Have you installed the openoffice.org(2)-kde package from the repositories, there's one for both 1.1.3 and the 2.0 beta version of OOo. This should help somewhat in making OOo look more at home in KDE

As far as I know there is no 1.1.4 deb-package for (k)ubuntu[/QUOTE]

but the OOo 2.0 beta is well, beta.
i use it for work
is the beta stable?

because i'll not try a nicer look if there's risk of crashing or whatever.

---

### Post by getaceres on 2005-09-12
[QUOTE=yoloosis]OOo seems to be programmed with gtk, so I don't think is possible to make it look like a KDE application...[/QUOTE]

No, it's programmed using it's own toolkit (like Firefox). But as a GNOME-Centric distribution, Ubuntu only comes with the GNOME frontend. There is a KDE front-end for the 1.1.3 version (I had it installed in Debian) but I can't find it in Ubuntu.

---

### Post by treris on 2005-09-12
there is also an openoffice.org-kde for the 1.1.3 (stable) release available through the repositories. 
I've been using OOo 2.0 beta now for a while and I have had no stability issues with it yet, although I have found a couple of minor bugs in comparison with the 1.1.3 release, nothing serious though and usually in functions that hardly anybody uses

however if you're dead set on getting the office applications blend in with kde, why not try Koffice?

I havent tried that yet, but maybe someone could give some information about the pros and cons of koffice in comparison with OOo??

---

### Post by getaceres on 2005-09-12
[QUOTE=treris]
I havent tried that yet, but maybe someone could give some information about the pros and cons of koffice in comparison with OOo??[/QUOTE]

Cons:

1. It does not open Microsoft Office documents as well as OpenOffice.
2. It does not have half of the features OpenOffice has.
3. It's way more unstable (at least for me) than OpenOffice beta.

Pros:
1. Integrated with KDE.
2. It's very very much lighter (faster startup, less memory used).

---

### Post by treris on 2005-09-12
Thanks for the info on Koffice!!

I think I'll stay with OOo 2.0 then because most people I know and exchange files with use MS Office, unfortunately I haven't been able to convince them that (k)ubuntu really is much better than winblows, hahahahaha ;-)

---

### Post by yhotg on 2005-09-12
[QUOTE=getaceres]No, it's programmed using it's own toolkit (like Firefox). But as a GNOME-Centric distribution, Ubuntu only comes with the GNOME frontend. There is a KDE front-end for the 1.1.3 version (I had it installed in Debian) but I can't find it in Ubuntu.[/QUOTE]

what's the KDE front-end for the 1.1.3 then?
if u mean  openoffice.org-kde for the 1.1.3 , i have it installed and doesn't change no thing. It looks exactly as err gnome. ( if i would like how gnome looks i'll have install ubuntu and not kubuntu lol)

well so, the OOo 2 beta is sufficient stable ? and it is the one in the repositories? or the version in the OOo site is newer?

---

### Post by shakin on 2005-09-12
[QUOTE=yhotg]what's the KDE front-end for the 1.1.3 then?
if u mean  openoffice.org-kde for the 1.1.3 , i have it installed and doesn't change no thing. It looks exactly as err gnome. ( if i would like how gnome looks i'll have install ubuntu and not kubuntu lol)

well so, the OOo 2 beta is sufficient stable ? and it is the one in the repositories? or the version in the OOo site is newer?[/QUOTE]

Try the OOo beta from openoffice.org. The installer works fine. I installed it into /opt/ooo2/ to keep it completely separate from 1.3 so I can go back to 1.3 if I want to.

---

### Post by mlomker on 2005-09-12
I greatly prefer Koffice 1.4 to Openoffice.  The older version of Koffice couldn't open a lot of MSWord documents but I've had no problems with the newer one.

To make gnome apps look better in KDE, make sure you've installed the gtk-qt-engine package using Synaptic.  It'll create a new menu pick in Kcontrol under Appearance and Themes, called GTK Styles and Fonts.

---

### Post by yhotg on 2005-09-13
[QUOTE=mlomker]I greatly prefer Koffice 1.4 to Openoffice.  The older version of Koffice couldn't open a lot of MSWord documents but I've had no problems with the newer one.

To make gnome apps look better in KDE, make sure you've installed the gtk-qt-engine package using Synaptic.  It'll create a new menu pick in Kcontrol under Appearance and Themes, called GTK Styles and Fonts.[/QUOTE]

the only package i did find is gtk2-engines-gtk-qt

do u mean this one?

---

### Post by earlycj5 on 2005-09-13
[QUOTE=yhotg]the only package i did find is gtk2-engines-gtk-qt

do u mean this one?[/QUOTE]


That's the package.

There's also a KDE integration package in the repositories for OOo2 that makes it look splendid.  Unfortunately it only works with the version of OOo2 from the repositories which is hopelessly outdated.  :(

I've got the most recent version, it's fast enough for me to use from time to time.  Though I'll admit I have Crossover Office so I just use my copy of Office2000 most of the time anyway.

---

### Post by mlomker on 2005-09-14
[QUOTE=yhotg]the only package i did find is gtk2-engines-gtk-qt

do u mean this one?[/QUOTE]

Right.  It's hard to remember names like that from memory.    :smile:

---

### Post by yhotg on 2005-09-14
[QUOTE=shakin]Try the OOo beta from openoffice.org. The installer works fine. I installed it into /opt/ooo2/ to keep it completely separate from 1.3 so I can go back to 1.3 if I want to.[/QUOTE]

did u make a multiuser or simple user install ?
i tried to make a multiuser in /opt/OOo/ and had lot of permission problems. never found out why.
(as i did need it fast and working nice at least for me, i got the version from the repositories  but is kind of old lol)

---

### Post by treris on 2005-09-14
I found the installer that's on the regular openoffice site to be rather outdated, but in the document project of openoffice.org I found another installation guide which is a lot more up to date
it's a pdf file which completely explains the installation process for just about every OS out there including debian based os's, which works out fine for (k)ubuntu.

the guide is [here](http://documentation.openoffice.org/setup_guide2/2.x/en/SETUP_GUIDE_draft.pdf)

---

### Post by yhotg on 2005-09-17
[QUOTE=treris]I found the installer that's on the regular openoffice site to be rather outdated, but in the document project of openoffice.org I found another installation guide which is a lot more up to date
it's a pdf file which completely explains the installation process for just about every OS out there including debian based os's, which works out fine for (k)ubuntu.

the guide is [here](http://documentation.openoffice.org/setup_guide2/2.x/en/SETUP_GUIDE_draft.pdf)[/QUOTE]

thank u man,
 :grin: 

yhotg

---

