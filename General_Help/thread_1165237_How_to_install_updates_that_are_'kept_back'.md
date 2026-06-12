---
title: "How to install updates that are 'kept back'?"
date: 2009-05-20
forum: General Help
---

### Post by joey-elijah on 2009-05-20
Update manager shows some greyed out updates that are 'kept back'. Whilst i appreciate it keeping them back for me, i'd rather like to install them because i can't currently use openoffice! (They're all open-offer related, such as openoffice-core, openoffice-base, etc)

Why are they kept back and how do i force install them?

---

### Post by mcduck on 2009-05-20
Packages are usually kept back because some dependency can't be satisfied. What version of Ubuntu you are using, and have you added any extra repositories apart from Ubuntu's official ones?

You could also try updating with Synaptic, (or by running "sudo apt-get update && sudo apt-get dist-upgrade". This allows the package manager to do a bit more to solve dependencies than what the Update Manager can do.

(Update manager & "apt-get upgrade" can only replace packages or add new ones, while Synaptic & "apt-get dist-upgrade" can also remove packages if necessary).

Although your problem is most likely a result from using wrong repositories.

---

### Post by joey-elijah on 2009-05-20
Hey, yeah i added (via ubuntu tweak) a repo for OpenOffice 3.1 and updated and these packages have been kept back siince. I'm using 9.04 (64 bit, not that it matters)

---

### Post by growled on 2009-05-20
You first need to first uninstall OO 3.01 and some of it's dependencies. I use this tutorial and everything worked fine.

[http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)

---

