---
title: "what's wrong with bibus installation"
date: 2009-05-16
forum: General Help
---

### Post by jingqi on 2009-05-16
jqduan@jqduan-laptop:~$ sudo apt-get install bibus
[sudo] password for jqduan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  bibus: Depends: python-central (>= 0.6.11) but 0.6.7ubuntu0.1 is to be installed
E: Broken packages

---

### Post by oldtime on 2009-09-30
What version of Ubuntu are you running?

I just got done fixing some bibus install and configuration problems, so it's fresh on my mind.

I was trying to install bibus 1.4.3-3 on 8.04 Hardy and kept running into a python dependency issue with my python-central. Somebody clued me into the fact that 1.4.3-3 doesn't run on Hardy, so I got the 1.4.2-1_all.deb package from [http://sourceforge.net/projects/bibus-biblio/files/](http://sourceforge.net/projects/bibus-biblio/files/) instead and it installed fine.

---

### Post by aspergerian on 2009-10-31
> **oldtime said:**
> What version of Ubuntu are you running?

I just got done fixing some bibus install and configuration problems, so it's fresh on my mind.

I was trying to install bibus 1.4.3-3 on 8.04 Hardy and kept running into a python dependency issue with my python-central. Somebody clued me into the fact that 1.4.3-3 doesn't run on Hardy, so I got the 1.4.2-1_all.deb package from [http://sourceforge.net/projects/bibus-biblio/files/](http://sourceforge.net/projects/bibus-biblio/files/) instead and it installed fine.

I too am running Heron. I went to the url you recommended and found 1.4.2, but that lists two items with Win32. Is either appropriate for installation via Heron?

---

### Post by oldtime on 2009-11-11
I haven't checked the forum in a while! Sorry about not getting back sooner.
I think I see what you're looking at on the page. Keep scrolling down PAST the win32-exe files. There is a bibus_1.4.2-1_all.deb package down past the win32 stuff. I was able to download it and then my installer ran it without a glitch.
How'd it go?

---

