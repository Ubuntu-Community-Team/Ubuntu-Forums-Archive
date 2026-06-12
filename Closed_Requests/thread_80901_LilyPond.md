---
title: "LilyPond"
date: 2005-10-23
forum: Closed Requests
---

### Post by Minyaliel on 2005-10-23
LilyPond is a music notation software which makes absolutely beautiful scores. And it's much easier to use than most notation software. I know you've already got one notation software in the repos, but LilyPond is by far the better one. Please, please include it in the repos. I'm sure I'm not the only music student who needs such a thing. I've already tried to download it from the software's original site, but with no success. Please.

---

### Post by AgenT on 2005-10-23
Lilypond 2.2.6 is available in Breezy. You may have to enable all the repositories as it is available in universe.

---

### Post by Minyaliel on 2005-10-26
Huups alright thanks :)

---

### Post by fdimmling on 2005-11-04
[QUOTE=AgenT]Lilypond 2.2.6 is available in Breezy. You may have to enable all the repositories as it is available in universe.[/QUOTE]

That's true. But the version available - 2.2.6 - is absolutely outdated. 2.6.4 is the actual one, 2.4.6 is considered as _old_ and 2.2.6 as _ancient_. Since the program was improved considerably it should be worth being upgraded.

Friedrich

---

### Post by linuxted on 2005-11-07
[QUOTE=fdimmling]That's true. But the version available - 2.2.6 - is absolutely outdated. 2.6.4 is the actual one, 2.4.6 is considered as _old_ and 2.2.6 as _ancient_. Since the program was improved considerably it should be worth being upgraded.

Friedrich[/QUOTE]

I wonder why such an old version is used for Ubuntu 5.1.   I really hope the administrators of Ubuntu consider using the latest stable code (2.6.4).

I noticed a similar situation with the other music-notation language (abc)

off my soapbox now...

---

### Post by jdong on 2005-11-09
[http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=all&subword=0&exact=1&arch=any&releases=all&case=insensitive&keywords=lilypond&searchon=names](http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=all&subword=0&exact=1&arch=any&releases=all&case=insensitive&keywords=lilypond&searchon=names)
[http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=lilypond](http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=lilypond)

Ubuntu is lagging behind indeed, but once it gets into Dapper, come bug me again about it and I'll file the backport for it!


Meanwhile, I've already poked some MOTU's about investigating the problem.

---

### Post by jdong on 2005-11-09
UPDATE:  I've already made the right contacts with the devs, they'll fix it.

Accepted.

---

### Post by Gustav on 2005-11-10
great!!!

---

### Post by fdimmling on 2005-11-10
[QUOTE=jdong]UPDATE:  I've already made the right contacts with the devs, they'll fix it.

Accepted.[/QUOTE]

Thanks a lot!!! 
BTW the same is true for the TeX system itself. Here also Breezy provides an antiquated version of tetex (2.x instead of 3.x) which lacks some important improvements.

Friedrich

---

### Post by dizzy1234 on 2005-11-10
Not wishing to sound impatient, but when will the new version be available, and how will we know when it is?

---

### Post by jdong on 2005-11-10
It's already in Dapper, but I need someone to test whether it builds under Breezy.

I'm having APT hell with archive.ubuntu.com, so I can't do it right now. Maybe another luckier dev, or when I get a chance over the weekend to really probe into the problem.

---

### Post by jdong on 2005-11-11
Tested, build queued. Just waiting for James to do the upload :).

---

### Post by dizzy1234 on 2005-11-11
Nice one.

Slightly off topic, but I tried to compile the source for lilypond 2.6.3 myself but got an error message to the effect that no suitable C compiler could be found. Bearing in mind I'm new to compiling, where would I go to find out about such things?

---

### Post by jdong on 2005-11-11
you need to run **sudo apt-get build-dep lilypond** to get all the packages necessary to build lilypond from source.

---

### Post by dizzy1234 on 2005-11-12
does that command work (with "lilypond" replaced with whatever) for any app I want to compile from source code?

---

### Post by jdong on 2005-11-12
[QUOTE=dizzy1234]does that command work (with "lilypond" replaced with whatever) for any app I want to compile from source code?[/QUOTE]

Yes. **apt-get source PACKAGENAME** fetches the source for a package and extracts it. **apt-get build-dep PACKAGENAME** fetches the dependencies for building that package. dpkg-buildpackage inside the extracted folder initiates build.

That's a simplistic look at how Backports works!

---

