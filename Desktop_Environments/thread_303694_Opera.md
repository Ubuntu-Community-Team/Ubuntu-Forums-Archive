---
title: "Opera?"
date: 2006-11-20
forum: Desktop Environments
---

### Post by stupidkid on 2006-11-20
How do I install Opera? I have the commercial repository.

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

However 

# apt-get install opera
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate


Yes I did a apt-get update.

Thanks.

---

### Post by melancholeric on 2006-11-20
I installed opera with [Automatix](http://www.getautomatix.com/).

---

### Post by meng on 2006-11-20
> **melancholeric said:**
> I installed opera with [Automatix](http://www.getautomatix.com/).
That's wonderful, but not everyone wants automatix.

---

### Post by Qew on 2006-11-20
If you can't find a satisfactory answer, then why not go to the [Opera site's download page](http://www.opera.com/download/) and download the relevant package. Use "sudo dpkg -i package.deb" (no quotes) to install the package. Alternatively, and maybe a better source than me, you can always go to [Ubuntu's own page on how to install Opera](https://help.ubuntu.com/community/OperaBrowser).

---

### Post by scxtt on 2006-11-20
don't know if it'll make any difference at all, but w/ the edgy commercial repos in your sources.list - try using aptitude ...

**sudo aptitude update**
**sudo aptitude search opera**
(if it's listed)
**sudo aptitude install opera**

this worked for me using dapper ... i've already got opera installed, but i changed my *dapper-commercial* to *edgy-commercial* and opera was still listed (tho that could just be cause it's already installed) ... only other reason would be that opera isn't in the edgy-commercial repos ... but just use the dapper version ...

---

### Post by stupidkid on 2006-11-22
> **scxtt said:**
> don't know if it'll make any difference at all, but w/ the edgy commercial repos in your sources.list - try using aptitude ...

**sudo aptitude update**
**sudo aptitude search opera**
(if it's listed)
**sudo aptitude install opera**

this worked for me using dapper ... i've already got opera installed, but i changed my *dapper-commercial* to *edgy-commercial* and opera was still listed (tho that could just be cause it's already installed) ... only other reason would be that opera isn't in the edgy-commercial repos ... but just use the dapper version ...

apt-get install wouldn't work, so how's aptitude any different? But I tried anyways and # aptitude search opera returned nothing.

Anyone else? I guess I could just download the package from opera.com, but I like managing programs with a package manager. 

Thanks.

---

### Post by Qew on 2006-11-23
Is there any reason why adding "deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free" (no quotes) to your sources.list isn't a good idea (it's mentioned in the link that I gave above)? All that does is install the version you'd get at the Opera site, but it's friendly for your package management needs.

---

### Post by stupidkid on 2006-11-23
> **Qew said:**
> Is there any reason why adding "deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free" (no quotes) to your sources.list isn't a good idea (it's mentioned in the link that I gave above)? All that does is install the version you'd get at the Opera site, but it's friendly for your package management needs.

oh haha, I didn't see that on the page. Cool that works, thanks. But I still dont' get why the "commercial" repository doesn't have opera. Did it get removed?

---

### Post by Qew on 2006-11-23
Sorry, I don't know if or why it was removed. I do remember it was said that the version on the commercial repository was a bit behind the times (9.00 instead of 9.02). I get my Opera from the site (I'm using the latest beta of 9.10), so can't really offer much more than that.

---

### Post by scxtt on 2006-11-23
not that it matters anymore, but ...

[http://archive.canonical.com/pool/main/o/opera/](http://archive.canonical.com/pool/main/o/opera/)

the *.deb for opera is there - you might have had issues w/ it if you used "edgy" in your sources.list and not "dapper", since the Packages.gz in edgy-commercial is empty ...

---

