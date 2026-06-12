---
title: "OpenOffice2 w/ Thesaurus"
date: 2005-11-27
forum: Deferred/Invalid Requests
---

### Post by snowmotion on 2005-11-27
Can we get OpenOffice2.0 in the official backports source with a thesaurus intact?

Using the OO2 packages from the [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) repository does not provide a thesaurus.

Thank you.

Snow

---

### Post by MartinG on 2005-11-27
It only seems to be available from the Debian repositories. Try this link (no guarantees):

[http://packages.debian.org/unstable/text/openoffice.org-thesaurus-en-us](http://packages.debian.org/unstable/text/openoffice.org-thesaurus-en-us)

---

### Post by jdong on 2005-11-29
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=openoffice.org2](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=openoffice.org2)

Not in Dapper yet...

As far as the Sid package, please use ubp-build.py to backport it before installing that deb.... I do **NOT** recommend installing packages straight from Debian or any other distro... The whole idea that debs work universally is the same as the idea that because it's in a zip file, the contents work on every platform that the zip could be extracted on!


You'll probably cause major breakage from mix and matching binaries from other distributions, which will eventually lead to a fresh install :)

---

### Post by MartinG on 2005-11-30
I note your comments re how to do it.  The major problem, which the script does not cover (why should it?), is that the Sid package, and the backported package from it both depend on openoffice.org-core, whereas the packages in [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/)
provide openoffice.org2-core (i.e. OOo2 has been renamed).  I had to hack the control file to get it to install.

[QUOTE=jdong]As far as the Sid package, please use ubp-build.py to backport it before installing that deb.... I do **NOT** recommend installing packages straight from Debian or any other distro... The whole idea that debs work universally is the same as the idea that because it's in a zip file, the contents work on every platform that the zip could be extracted on!


You'll probably cause major breakage from mix and matching binaries from other distributions, which will eventually lead to a fresh install :)[/QUOTE]

---

### Post by jdong on 2005-11-30
yeah, you can hack the files all you want.... Just make sure that it's built against the right distribution! That's what really matters here.

---

### Post by Limulus on 2005-12-09
[QUOTE=snowmotion]Using the OO2 packages from the [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) repository does not provide a thesaurus.[/QUOTE]
In the mean time, please see this thread: [http://ubuntuforums.org/showthread.php?p=557274](http://ubuntuforums.org/showthread.php?p=557274) (especially the second post ^_-)

---

