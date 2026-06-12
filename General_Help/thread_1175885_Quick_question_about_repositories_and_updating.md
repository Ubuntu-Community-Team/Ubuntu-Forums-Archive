---
title: "Quick question about repositories and updating"
date: 2009-06-01
forum: General Help
---

### Post by cody7002002 on 2009-06-01
What exactly are repositories? Are they collections of programs to download from? I have checked all the repositories in the software sources but I sometimes hear people talking about adding repositories. Are there any repositories that are recommended to add that aren't provided by default?

In ubuntu, do programs update automatically (say firefox or pidgin for example) or do you have to update them manually somehow? If not, are program updates listed in the update manager when they available?

---

### Post by michy99 on 2009-06-01
This explains repositories:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by cody7002002 on 2009-06-01
Ah, thanks well that answers my first question. Now what about additional repositories that one should add? Are there any? Also my question about updating programs still remains.

---

### Post by lovinglinux on 2009-06-01
> **cody7002002 said:**
> In ubuntu, do programs update automatically (say firefox or pidgin for example) or do you have to update them manually somehow? If not, are program updates listed in the update manager when they available?

They are updated automatically when you run the update manager, but depending on the software, only security updates are incorporated. For example, Firefox is always update when a new version is available, but other programs like OpenOffice are only updated when there are security patches.

If you want to keep a specific program updated, no matter what type of patch is available, then you might want to add a repository from the developer or from a Launchpad PPA Team. For example, I have the [PPA repository from Deluge Team](https://launchpad.net/~deluge-team/+archive/ppa), because I want to always have the latest version of Deluge. PPA are "Personal Package Archives", which means it is a personal repository used by software developers or people interested on compiling and distributing software.

> **cody7002002 said:**
> Are there any repositories that are recommended to add that aren't provided by default?

I can think only about [medibuntu repository](http://www.google.com/search?q=how+to+add+medibuntu+repository+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0), which has media related stuff, like codecs and players.

---

