---
title: "linux-image-386 held back"
date: 2006-01-12
forum: General Help
---

### Post by Tom Bentley on 2006-01-12
I installed breezy on server earlier this week. Following the initial install, I added universe (breezy and breezy-security) to my /etc/apt/source.list and installed some packages. Now aptitude is telling me that linux-image-386 and linux-restricted-modules-386 are held back.

I think the problem is that:
[LIST]
[*]linux-image-386 depends on linux-image-2.6.12-10-386
[*]linux-restricted-modules-386 depends on linux-restricted-modules-2.6.12-10-386
[/LIST]
and these are unresolved dependencies. 

As I understand it linux-image-386 always depends on the lastest kernel image, and similarly linux-restricted-modules-386 always depends on the lastest restricted modules.

I don't understand why these dependencies are broken though, nor what I can do to fix it.

Thanks!

Tom

---

### Post by hubbadub on 2006-01-12
Do a 
> Sudo apt-get dist-upgrade
That should let you download and install those files. Then a:
> Sudo apt-get -f install
Should fix any dependacy issues you are having.

---

### Post by Tom Bentley on 2006-01-13
Ah, that seems to have fixed the problem. Thanks very much!

---

