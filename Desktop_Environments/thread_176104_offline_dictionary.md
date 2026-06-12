---
title: "offline dictionary"
date: 2006-05-14
forum: Desktop Environments
---

### Post by rkakkar on 2006-05-14
during my windows days.. i used to have this beautiful app called WordWeb - 
[http://wordweb.info](http://wordweb.info). Its basically an **offline** dictionary which sits in your taskbar. When the program is in the tray you can look up a word in almost any program by pressing Ctrl+Alt+W or clicking on the icon.

i really really hope there is an ubuntu alternative.. any ideas? it has to be an offline dictionary since i'm on dial up :P

---

### Post by drl on 2006-05-14
Hi, rkakkar.

I had not seen wordweb before, but I can see how such items are useful for a dial-up connection (although word**web** suggests online to me).

I am not in front of a Ubuntu box right now, but a Google search with:
> linux offline dictionary -attack
lists a number of possibilities, one interesting one being pointed to is *stardict *at:
```
http://swobodin.fedora-tn.org/?p=140
```
but search for yourself to see things that I might easily have missed ... cheers, drl

---

### Post by hassan_saeed on 2006-11-15
I was very happy to see i can use wine to install and run wordweb dictionary free version.
the dictionary can be downloaded from:
[http://wordweb.info/free/]("http://wordweb.info/free/")

An .exe file in the install directory named wwnotray.exe can be run using wine after the program has been installed.

This has solved my problem for having a good dictionary offline.

---

### Post by urukrama on 2006-11-15
Try StarDict, it is quite nice. The base is in the repos (find it through Synaptic), and the dictionaries can be found on [Sourceforge]("http://stardict.sourceforge.net/").

The [Oxford Advanced learners]("http://prdownloads.sourceforge.net/stardict/stardict-oald-2.4.2-1.noarch.rpm?download") dictionary is available for free, as is a [Merrian Webster]("http://prdownloads.sourceforge.net/stardict/stardict-merrianwebster-2.4.2-1.noarch.rpm?download"). There are a lot more dictionaries available, and in many languages. There is [English - Hindi]("http://stardict.sourceforge.net/Dictionaries_misc.php") one, but no Urdu I'm afraid.

Installation instructions for the dictionaries can be found [here]("http://anatilim.googlepages.com/index.html").

If you run Dapper, you'll have to install the base from the repos, and not from sourceforge, as that version won't work in Dapper. I'm not sure about Edgy, but the package from sourceforge might work (or is it already updated in the repos?).

---

