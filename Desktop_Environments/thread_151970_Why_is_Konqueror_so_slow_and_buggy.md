---
title: "Why is Konqueror so slow and buggy?"
date: 2006-03-28
forum: Desktop Environments
---

### Post by Mau on 2006-03-28
I installed Kubuntu a month or two ago, and so far I use it all the time.  I saw that Konqueror was both a file browser and web browser, and I was eager to try it out (and see how it differed from Explorer).  

Anyways, the file browsing for Konqueror works fine.  But, something must be wrong for the web browsing.  First of all, compared to Firefox, it takes about 10 times longer to download the pages (probably because it renders after the whole page is downloaded, where Firefox renders on the fly), and after it downloads it, it usually fails to load images, style sheets, or even render the entire page.  What's the deal?

I have screwed around with all the preferences, but no-luck.  Firefox works fine, but Konqueror just seems like it slapped together.  What's up and any ideas on how to fix this? ](*,) 

BTW, thanks for all the help -- this is a great community.

---

### Post by Ptero-4 on 2006-03-28
Are you using the default breezy KDE (3.4.3) or the Dapper one (3.5.1)? I noticed that on 3.5.1 things tend to be slow while 3.4.3 is a bit faster, probably is b/c 3.4.3 is stable and 3.5.1 have some quirks.

---

### Post by Mau on 2006-03-28
I'm running Breezy, but with KDE 3.5.x.  However, I remember having the same problems from 3.4.x.

---

### Post by aysiu on 2006-03-28
Konqueror buggy--sure.

The errors you're talking about--the first I've read of them.

---

### Post by Mau on 2006-03-28
[QUOTE=aysiu]The errors you're talking about--the first I've read of them.[/QUOTE]

That's what weird about it.  I have searched Google expecting to find page-after-page with my same problem, but nothing.  I just did a default install, and I have all the default options, and there's the problem.  The problem is a rendering issue (I can view source fine), so it's a software issue.

Any ideas on what could be causing them (let's forget about fixing them :-k )?

---

### Post by aysiu on 2006-03-28
If you really want to do detective work on it, try creating a new "dummy" user. See if that user has the same Konqueror problem.

---

### Post by ltmon on 2006-03-28
Some people get this problem because Konqueror has IPV6 turned on by default.  It is slower to resolve (?) on some networks or some such technobabble.  In any case, without many (if any) sites using IPV6 it's quite safe to turn off to give it a go.

See: [http://ubuntuforums.org/showthread.php?t=76518](http://ubuntuforums.org/showthread.php?t=76518)

L.

---

### Post by Mau on 2006-03-29
I tried the IPV6 switch, and that just killed my net access.  So I reverted.

Anyways, I decided just to try and re-install Konqueror.  I removed it fine, but now I cannot reinstall (the error message basically tells me 1 != 1):

```
carl@carl:~$ sudo apt-get install konqueror
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  konqueror: Depends: kcontrol (= 4:3.5.0-0ubuntu0breezy1) but 4:3.5.1-0ubuntu0breezy1 is to be installed
             Depends: kdebase-kio-plugins (= 4:3.5.0-0ubuntu0breezy1) but 4:3.5.1-0ubuntu0breezy1 is to be installed
             Depends: kdesktop (= 4:3.5.0-0ubuntu0breezy1) but 4:3.5.1-0ubuntu0breezy1 is to be installed
             Depends: kfind (= 4:3.5.0-0ubuntu0breezy1) but 4:3.5.1-0ubuntu0breezy1 is to be installed
E: Broken packages
```

Any ideas on how to get Konqueror back?

---

### Post by aysiu on 2006-03-29
It sounds as if you have conflicting repositories.

Can you post your /etc/apt/sources.list? Or, better yet, [get a new one](http://www.psychocats.net/ubuntu/sources)?

---

### Post by Mau on 2006-03-29
I got a new one (as I was having problems with the one I had).

New one:
```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 

```

Old one (backed up):
```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

deb http://people.ubuntu.com/~doko/OOo2 ./

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

deb http://deb.opera.com/opera/ etch non-free

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://kubuntu.org/packages/kde35 breezy main
## created by arniemaxremoved

## modified 
deb http://kubuntu.org/packages/kde352 breezy main
deb ftp://bolugftp.uni-bonn.de/pub/kde/stable/3.5.2/kubuntu breezy main
deb http://www.mirrorservice.org/sites/ftp.kde.org/pub/kde/stable/3.5.2/kubuntu breezy main
deb http://mirror.cc.columbia.edu/pub/software/kde/stable/3.5.2/kubuntu breezy main
```

I was then able to install Konqueror just fine, except now I'm running Konqueror 3.4 on KDE 3.5.  Before, I had Konqueror 3.4 on KDE 3.5.  Is that a big deal?

---

### Post by aysiu on 2006-03-29
[QUOTE=Mau]
I was then able to install Konqueror just fine, except now I'm running Konqueror 3.4 on KDE 3.5.  Before, I had Konqueror 3.4 on KDE 3.5.  Is that a big deal?[/QUOTE] [This](http://kubuntu.org/announcements/kde-352.php) may help.

---

### Post by Simian on 2006-03-29
I love Konqueror but I find that some pages don't render properly (not often though). For instance I am currently looking at the Paypal page and the menu is all wrong. Some part of the menu are overlapping and some parts of the menu are only partially displayed. It's odd.

---

### Post by Mau on 2006-03-29
I upgraded KDE to 3.5.2 via dist-upgrade, and it brought Konqueror back up to speed.  It also seems to have fixed some rendering issues, so everything is loading fine now.

However, two problems now:
- Still really slow to load pages (I'm pretty sure it's a rendering problem).
- Whenever I click on a link, it prompts to load Kate to show the source code.  I can type in the address bar just fine, but I cannot click on links.  

Odd.  I will try the new user technique later tonight.

---

### Post by aysiu on 2006-03-29
[QUOTE=Mau]
- Whenever I click on a link, it prompts to load Kate to show the source code.  I can type in the address bar just fine, but I cannot click on links.[/QUOTE] Check your file associations for HTML/HTM. If you have Kate as the default program, Konqueror will want to open HTML pages with it. That's why I don't use Konqueror for the web.

I use Kate to open HTML and edit it.

I use Firefox to browse.

---

### Post by Mau on 2006-03-30
The File Associations did it.  Konqueror now works quite well and loads about the same speed of Firefox now.

The one problem is that it doesn't load the style sheet for Slashdot.  It seems like this problem would have been reported, and people would know about it.  Any ideas?

---

