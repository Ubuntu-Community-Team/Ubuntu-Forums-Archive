---
title: "no thesaurus in OpenOffice"
date: 2005-11-04
forum: Desktop Environments
---

### Post by Technoviking on 2005-11-04
I don't not have a thesaurus in OpenOffice in Breezy, is this normal. If not, is there a fix?

Mike

---

### Post by angkor on 2005-11-04
apt-cache search openoffice | grep thesaurus
openoffice.org-thesaurus-de - German Thesaurus for OpenOffice.org
**openoffice.org-thesaurus-en-us - English (US) Thesaurus for OpenOffice.org**
openoffice.org-thesaurus-it - Italian Thesaurus for OpenOffice.org
thescoder - compiler for OpenOffice 1.x thesaurus files


This doesnt work?

---

### Post by Technoviking on 2005-11-04
Wants to install OpenOffice 1

dbasinge@pheonix:~$ apt-cache search openoffice | grep thesaurus
openoffice.org-thesaurus-de - German Thesaurus for OpenOffice.org
openoffice.org-thesaurus-en-us - English (US) Thesaurus for OpenOffice.org
openoffice.org-thesaurus-it - Italian Thesaurus for OpenOffice.org
thescoder - compiler for OpenOffice 1.x thesaurus files
dbasinge@pheonix:~$ sudo apt-get install openoffice.org-thesaurus-en-us
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libneon23 openoffice.org openoffice.org-bin openoffice.org-l10n-en
  openoffice.org1-debian-files
Suggested packages:
  openoffice.org-help menu ooqstart-gnome oooqs-kde unixodbc
  openoffice.org-hyphenation openoffice.org-mimelnk openoffice.org-gtk-gnome
  openoffice.org-kde openoffice.org-gnomevfs xlibmesa-gl libgl1 openclipart
  openoffice.org-hyphenation-en openoffice.org-help-en
The following packages will be REMOVED:
  mozilla-openoffice.org openoffice.org2 openoffice.org2-base
  openoffice.org2-calc openoffice.org2-common openoffice.org2-core
  openoffice.org2-draw openoffice.org2-evolution openoffice.org2-gnome
  openoffice.org2-impress openoffice.org2-l10n-en-us openoffice.org2-math
  openoffice.org2-writer python-uno
The following NEW packages will be installed:
  libneon23 openoffice.org openoffice.org-bin openoffice.org-l10n-en
  openoffice.org-thesaurus-en-us openoffice.org1-debian-files
0 upgraded, 6 newly installed, 14 to remove and 0 not upgraded.
Need to get 55.5MB of archives.
After unpacking 4067kB disk space will be freed.

---

### Post by Ampersand on 2005-11-04
I can't seem to find the openoffice2 thesauruses in Synaptic, but there are a few for OO.o (which seem to require the uninstallation of OO.o2). Looks like it is normal...

---

### Post by angkor on 2005-11-04
[QUOTE=Mike Basinger]Wants to install OpenOffice 1
[/QUOTE]

ah, my bad. Didn't notice it was for 1 only...hmm...

---

### Post by skybum on 2005-11-05
Just a note to say that I'm missing a thesaurus, too, and am feeling very grumpy about it.

Surely these are isolated bugs?  Because if *every* Ubuntu user were missing their thesaurus, I would hope that there would be more of an uproar.  Or is the thesaurus really that specialized of a function?

---

### Post by peanut butter on 2005-11-06
as far as i know their isint one forOO.o 2
i would suggest using Abiword(also opensource) or ifyou have kde (or a broadband connection) you could try koffice.:smile:

---

### Post by jasay on 2005-11-06
Hmm.  I have a thesaurus, but I have 2.0 not 1.9.129.:???:

---

### Post by kperkins on 2005-11-06
nope, no thesaurus here either.
The US english one is supposed to be included in OOo, according to the OOo site.  (and Dictooo--the extension to grab new dictionaries and thesuari--seems to be not working either.)

---

### Post by nozdormu on 2005-12-03
[QUOTE=skybum]Just a note to say that I'm missing a thesaurus, too, and am feeling very grumpy about it.

Surely these are isolated bugs?  Because if *every* Ubuntu user were missing their thesaurus, I would hope that there would be more of an uproar.  Or is the thesaurus really that specialized of a function?[/QUOTE]

I'm bringing this back up because I've searched everywhere and cannot find anything about how to get a Thesaurus for OpenOffice.org 2 in Breezy.  Hell, it should have one, the tools menu lists Thesaurus, but it is greyed out.  This is a pretty critical oversight in my book.

---

### Post by dcstar on 2005-12-03
[QUOTE=nozdormu]I'm bringing this back up because I've searched everywhere and cannot find anything about how to get a Thesaurus for OpenOffice.org 2 in Breezy.  Hell, it should have one, the tools menu lists Thesaurus, but it is greyed out.  This is a pretty critical oversight in my book.[/QUOTE]
The DicOO0 utility macro works well for me in installing all these components:

[http://lingucomponent.openoffice.org/download_dictionary.html](http://lingucomponent.openoffice.org/download_dictionary.html)

---

### Post by Limulus on 2005-12-09
[QUOTE=Mike Basinger]I don't not have a thesaurus in OpenOffice in Breezy, is this normal. If not, is there a fix?[/QUOTE]
Please see this thread: [http://ubuntuforums.org/showthread.php?p=557274](http://ubuntuforums.org/showthread.php?p=557274) (especially the second post ^_-)

---

### Post by Michael Steinberg on 2005-12-19
Thanks on the wizard help; so far it seems to work fine in the Ubuntu-installed OOo pseudo-2.

I haven't tried downloading the REAL 2.0 partially because Ubuntu's tweaking of the interface (or is it Gnome's?) is much more pleasant than OOO's own icons, etc. Anyone who's done the upgrade willing to post a screenshot?

Michael Steinberg

---

### Post by Limulus on 2005-12-19
[QUOTE=Michael Steinberg]Thanks on the wizard help; so far it seems to work fine in the Ubuntu-installed OOo pseudo-2. I haven't tried downloading the REAL 2.0 partially because Ubuntu's tweaking of the interface (or is it Gnome's?) is much more pleasant than OOO's own icons, etc. Anyone who's done the upgrade willing to post a screenshot?[/QUOTE]

The official 2.0 for Linux should look pretty much like this: [http://www.openoffice.org/screenshots/ooo20/linux/index.html](http://www.openoffice.org/screenshots/ooo20/linux/index.html)

The 2.0 Ubuntu version you get when using *deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./* as a repository looks like this:

[http://members.shaw.ca/Limulus/OOo2.png](http://members.shaw.ca/Limulus/OOo2.png)
[http://members.shaw.ca/Limulus/OOo2about.png](http://members.shaw.ca/Limulus/OOo2about.png)

---

