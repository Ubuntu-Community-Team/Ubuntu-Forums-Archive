---
title: "Too many language locales mess up in firefox and thunderbird"
date: 2008-09-27
forum: Desktop Environments
---

### Post by OrelEagle on 2008-09-27
Hello,

I'm on Ubuntu 8.04.1 and I installed language support for English, German and French. It seems I got quite a lot of unnecessary locales as well:

Output of locale -a
```
C
de_AT.utf8
de_BE.utf8
de_CH.utf8
de_DE.utf8
de_LU.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
fr_BE.utf8
fr_CA.utf8
fr_CH.utf8
fr_FR.utf8
fr_LU.utf8
POSIX
```
 
The only ones I want are en_GB, fr_FR, and de_DE. It's not a big problem for most uses, but it's disturbing in firefox and thunderbird, as 10 different locales show up instead of 3…

Is there a way to select only the ones I need?

---

### Post by farchumbre on 2009-04-18
Hi,
I have the same problem,
Did you find any solution?
thanks

---

### Post by MZBKA on 2009-06-21
Bump.  Has anybody found a solution to this?

---

### Post by atomizer on 2009-06-21
maybe [this link]("http://www.ubuntugeek.com/how-to-select-and-generate-locales-on-ubuntu.html") will help.....

you probably just have to remove some locales

---

### Post by JHAx86 on 2010-11-07
Old Thread, but since google brings me to here I think nobody has answer a similar question in the forum. Having too many dictionaries increases the time you need to find the one you want.

[quote="atomizer"]
maybe [this link]("http://www.ubuntugeek.com/how-to-select-and-generate-locales-on-ubuntu.html") will help.....

you probably just have to remove some locales     
[/quote]

Remove unused locales and then run **dpkg-reconfigure locales** is a good idea but you still have many dictionaries in Firefox.

The solution I found is delete unused dictionaries from **/usr/share/myspell/dicts**. *.dic and *.aff files, and leave only the three languages I use: en-US.dic, en-US.aff, es.dic, es-ES.dic, es-ES.aff. Backup the whole directory before delete anything.

---

### Post by kryos on 2010-11-07
Through Synaptic, mark all unused language packs for complete removal and apply.  Eliminates their local upgrades as well.

---

### Post by Andrew_P on 2013-03-10
This is obviously a long-standing bug in Firefox.  I have SeaMonkey installed on the same machine with Ubuntu 10.04 LTS, but it has never exhibited this problem.  I have only the en and en-US dictionaries shown in Edit / Preferences / Languages and that's all that shows up in the context menu when I'm entering text in a Web form.  Firefox 19.0.2, on the other hand, showed something like two dozen different variations of English, German and Latvian, and although I have German and Latvian dictionaries installed on the system for word processing, I never selected either of these languages for spelling checks in Firefox.  Moreover, Firefox showed *duplicate entries* for several variations of English and German, and every time I would enter text in a Web form, it would *randomly* choose one of the languages for spell-checking. 

There's a relevant discussion at [http://www.linuxforums.org/forum/miscellaneous/161789-solved-too-many-languages.html]("http://www.linuxforums.org/forum/miscellaneous/161789-solved-too-many-languages.html"), wherein a work-around solution was to remove links to the unwanted dictionaries from /usr/share/myspell.  Mind you, *these are just symbolic links to the dictionaries, not the dictionary files*, so by removing the symbolic links one isn't actually uninstalling anything from the system.  (I didn't actually delete the links; I just created a folder named "hidden" in /usr/share/myspell and dragged the unwanted icons into that folder.)  By doing this, i was able to prune the number of languages shown in the Firefox context menu down to something more reasonable &#8212; a single instance of each of en-US, en-CA, en-GB, de-DE and lv-LV.  I never did have German or Latvian selected in Firefox, and still only show "en" under Edit/Preferences/Content/Languages, so there's no reason why it should ever have shown all the different variations in the context menu.  I noticed in Synaptic that I have duplicate language packs installed for GNOME and KDE, but I don't know if the duplicate symbolic links in /usr/share/myspell were because of that.

Has a bug report *ever* been filed with Bugzilla on this issue?  The problem has been reported by Firefox users in various Linux distributions, not just Ubuntu, so it doesn't make sense to filter it through Launchpad in the hope that it might eventually bubble up to the level of Bugzilla and catch the attention of Firefox developers.

---

### Post by Andrew_P on 2013-03-10
> **kryos said:**
> Through Synaptic, mark all unused language packs for complete removal and apply.  Eliminates their local upgrades as well.

That's not relevant to this problem.  The entries are appearing in the Firefox context menu only for variations of the languages needed on the system, such as en-GB, en-US, en-AU, en-ZA, en-CA, etc., where only one version of English should be shown, but Firefox shows *all* of them.

---

### Post by JRV on 2013-03-11
This tutorial explains the use of localepurge to remove unneeded locales.

[http://ubuntuforums.org/showthread.php?t=1867813](http://ubuntuforums.org/showthread.php?t=1867813)

---

