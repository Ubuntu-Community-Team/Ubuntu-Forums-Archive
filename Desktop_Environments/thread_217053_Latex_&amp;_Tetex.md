---
title: "Latex &amp; Tetex"
date: 2006-07-16
forum: Desktop Environments
---

### Post by RudolfMDLT on 2006-07-16
Hi,

I need to use Tetex. In Synaptic when I select tetex from the repositries and try to download it I get the following error:

> The following packages have unresolved decencies. Please make sure that all requires repositories are added and enabled in the preferences.

tetex-base:
 Depends: tex-common (>=0.12) but it is not installable

As far as I know I have added all the repositories that I can tick. Any help would be very appreciated. How can I download Tetex?

(If any body is using an alternative that would be fine aswell! Thnx!)

---

### Post by jordilin on 2006-07-16
I have installed tetex without any problem. I have the following sources.list , so you can compare with yours:
```
deb http://es.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://es.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://es.archive.ubuntu.com/ubuntu/ dapper universe multiverse
 deb-src http://es.archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://es.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
 deb http://security.ubuntu.com/ubuntu dapper-security universe
 deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by RudolfMDLT on 2006-07-16
Thnx for the help jordilin!,

but in my list all sources are un-compented, even the back ports. Can yourself or anybody els think of another problem?

---

### Post by vigleik on 2006-07-16
What happens if you use jordilin's sources list? Having too many sources could lead to trouble as well, maybe you were too quick to enable all of them.

Vigleik

---

### Post by jordilin on 2006-07-16
Perhaps the problem comes with enabling the backports source. Disable backports, then do an apt-get update and try again.

---

### Post by hajk on 2006-07-16
You could consider installing the TeXLive2005 distribution as an alternative to teTeX, since teTeX is no longer maintained by Thomas Esser. Check [www.tug.org](www.tug.org) for download/install instructions... I've done this myself already, after purging any of the teTeX packages. 

TeXLive packages are already present in Debian unstable, and presumably they will be in Ubuntu Edgy (and may be in Dapper backports). They all require the tex-common package as well, but installing directly from the TeXLive2005 CD image does not (so would solve your problem).

---

### Post by jordilin on 2006-07-16
> **hajk said:**
> You could consider installing the TeXLive2005 distribution as an alternative to teTeX, since teTeX is no longer maintained by Thomas Esser. Check [www.tug.org](www.tug.org) for download/install instructions... I've done this myself already, after purging any of the teTeX packages. 

TeXLive packages are already present in Debian unstable, and presumably they will be in Ubuntu Edgy (and may be in Dapper backports). They all require the tex-common package as well, but installing directly from the TeXLive2005 CD image does not (so would solve your problem).

I've been really surprised as I didn't know these news. I've gone to TUG and see that I can download TExLiveCd from ctan but it provides two packages:
texlive2005-inst-20051102.iso.zip
and
texlive-inst.iso.zip
Which one have you downloaded?

---

### Post by hajk on 2006-07-16
> **jordilin said:**
> I've been really surprised as I didn't know these news. I've gone to TUG and see that I can download TExLiveCd from ctan but it provides two packages:
texlive2005-inst-20051102.iso.zip
and
texlive-inst.iso.zip
Which one have you downloaded?

The texlive2005-inst-20051102.iso.zip. After downloading (takes a while), you must first unzip the archive, and then you can burn it to CD as an image (just as you did with the Dapper liveCD). Alternatively, it is possible to mount the image without burning it to CD, and install from there (I'm not entirely sure about the details of this last method).

---

### Post by RudolfMDLT on 2006-07-17
Thanks for all the replies guys, if I can't tetex to work I'll try the alternative. 

Thanks a lot!

---

### Post by rquint on 2006-07-17
U had the same problem and solved it by forcing synaptic to install tetex-base_3.0-15build1 instead of the dapper-updates' tetex-base_3.0-15ubuntu1.

---

### Post by RudolfMDLT on 2006-07-18
Thanks... but I have no idea how to force synaptic to download something? How do I force synaptic to download something? Sorry, I'm still pretty new to Ubuntu.

---

### Post by jimscafe on 2006-08-17
I am new to TeX and new to Linux - but I am trying to learn TeX and LaTeX.

Why do you need to uninstall tetex to use LiveTeX?

I downloaded Kile but the when I compile it does not run the viewer saying 'Could not find the kviewerpart library' (I get round this by creating a pdf as an additional step)

Sorry if these seem basic questions but I have no idea where to look for the library.

When I installed tetex I had no idea how to run it - the manual seemed to just list its functions when I needed an idiots guide to using the basic modules - which is why I installed kile.

I don't feel confident I can install LiveTeX so might wait until it becomes a package.

I am also going to join the TeX user group.

---

### Post by hajk on 2006-08-18
> **jimscafe said:**
> I am new to TeX and new to Linux - but I am trying to learn TeX and LaTeX.

Why do you need to uninstall tetex to use LiveTeX?

Once you install TeXLive, the teTeX stuff isn't going to be used anymore... or at least it shouldn't. You should try and avoid mixing these distributions (many duplicate or almost duplicate files), so better to remove the teTeX packages.

> 
I downloaded Kile but the when I compile it does not run the viewer saying 'Could not find the kviewerpart library' (I get round this by creating a pdf as an additional step)

No need to take this extra step, since you can produce PDF output directly by using the "pdflatex" command.

> 
Sorry if these seem basic questions but I have no idea where to look for the library.

When I installed tetex I had no idea how to run it - the manual seemed to just list its functions when I needed an idiots guide to using the basic modules - which is why I installed kile.

You should get a book on LaTeX, there are many. I recommend a book that is not too technical, like "A Guide to LaTeX" by Kopka & Daly -- the slightly older 3rd edition is OK, is priced right, and still available at Amazon. Another suitable book is "Digital Typography using LaTeX" by Syropoulos et al.

> 
I don't feel confident I can install LiveTeX so might wait until it becomes a package.

I am also going to join the TeX user group.

It really isn't very difficult to install TeXLive, you can pretty well accept all the default settings. You've confident enough to install Ubuntu Linux, installing TeXLive doesn't take any more confidence than that.

Joining TUG is good for TUG, but I doubt whether it is good for a novice TeX user...

---

### Post by jimscafe on 2006-08-21
Thank you Hajk - I will try LiveTeX and I have ordered the book you recommended - a used version from Amazon, the new version is over $40!

---

