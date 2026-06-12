---
title: "Upgrade Mozilla-Firefox"
date: 2006-02-15
forum: Desktop Environments
---

### Post by CarlosinFL on 2006-02-15
I just installed 5.10 Ubuntu & wanted to get the latest version of Firefox 1.5. I tried using APT but the only thing it finds is 1.0.7.

Any suggestions?

Here is my sources.list:

[i]deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe[/i]

---

### Post by bluevoodoo1 on 2006-02-15
You have to do it by hand! But no fear, there is a guide and it's not very hard to accomplish!

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by bikeman on 2006-02-15
Or, you could just do it the easy way, with [Automatix.]("http://www.ubuntuforums.org/showthread.php?t=80295&highlight=automatix") This script is amazing and has worked perfectly for everything that I have used it for. Just make sure that your username has sudoer permissions, and read the whole thread for concerns with playing certain media (if you decide to use those features).

---

### Post by towsonu2003 on 2006-02-16
[quote=bikeman]  	Or, you could just do it the easy way, with Automatix. This script is amazing and has worked perfectly for everything that I have used it for. Just make sure that your username has sudoer permissions, and read the whole thread for concerns with playing certain media (if you decide to use those features)[/quote]
[quote=bluevoodoo1]  	You have to do it by hand! But no fear, there is a guide and it's not very hard to accomplish!
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)[/quote]

[joke]Incoming flamewar[/joke]

If you decide to use the wiki (Section 1), be sure to read it once before starting. It has some nice information on how to update afterwards.

---

### Post by CarlosinFL on 2006-02-16
[QUOTE=bluevoodoo1]You have to do it by hand! But no fear, there is a guide and it's not very hard to accomplish!

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)[/QUOTE]

I prefer to understand what I am doing step by step so this worked great!

---

### Post by bluevoodoo1 on 2006-02-16
[QUOTE=towsonu2003][joke]Incoming flamewar[/joke][/QUOTE]

HAHA!



[QUOTE=Carlwill]I prefer to understand what I am doing step by step so this worked great![/QUOTE]

Exactly! I fee the same way!

---

### Post by bikeman on 2006-02-16
> Originally Posted by Carlwill
I prefer to understand what I am doing step by step so this worked great!

Okay, I'll fess up.  A couple of months ago I knew didly about Linux and the CLI.  Automatix helped me get Ubuntu running well very quickly and easily.  Great for newbs.  However, I have learned a lot since then, and now am leaning towards agreeing with Carlwill.  I do want to understand what I am doing, but I do want it to work.  For example, setting up syncronization between Evolution and my Pocket PC was a nightmare.  Now it does most of what I want, but not all.  I would jump on a script like Automatix in a minute if it would work.  But, after already having done the Firefox upgrade with Automatix, I went through the wiki, and darned if I didn't actually learn something - how to set Firefox to upgrade to 1.5.0.1, which it would not do before (because of the permissions).

So I think that both have their place.  Ubuntu does not install a lot of packages by default, and not all of the how-tos indicate all of the needed packages to install.  Automatix may be a crutch, but it can help people get on their feet with Linux.  I really like Ubuntu, and am essentially Windows free at home!  Yeah!  :D

---

