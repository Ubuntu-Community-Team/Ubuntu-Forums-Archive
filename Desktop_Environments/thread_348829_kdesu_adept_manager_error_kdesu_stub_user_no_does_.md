---
title: "kdesu adept_manager error kdesu_stub: user no does not exist!"
date: 2007-01-29
forum: Desktop Environments
---

### Post by drushka on 2007-01-29
Hi all,

I'm a (l)user with error finding but not solving skills, so maybe some of you can help.
Thanks to all in advance, great forum!

After a recent upgrade in my laptop's edgy installation, I cannot launch adept from the menu anymore. I've investigated, so here is how it looks:

# adept_manager
(as root) works.
$ sudo adept_manager
(with xhosts +) works.
$ kdesu adept_manager
gives the following error message

> X Error: BadDevice, invalid or uninitialized input device 168
>   Major opcode:  148
>   Minor opcode:  3
>   Resource id:  0x0
> Failed to open device
> X Error: BadDevice, invalid or uninitialized input device 168
>   Major opcode:  148
>   Minor opcode:  3
>   Resource id:  0x0
> Failed to open device

So far so usual (and ugly to see everytime, what is this?) but now comes

> kdesu_stub: user no does not exist!

Now my name is not Dr. No and my username isn't either :) so I wonder how adept gets that idea. adept_manager --help-all didn't really enlighten me as to whether there's an option to give a username (and if it should be mine).

This problem has shown up simultaneously with a minor problem - some games I've added manually to the KDE start menu have stopped getting started because KDE doesn't seem to be aware of the $PATH variable anymore. Providing the full path for the launch of adept_manager in the menu does not fix the problem, however. (As shown above, where I have started kdesu adept_manager from the konsole, which knows my PATH.)

$ echo $PATH
.:/home/${USER}/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"

(I've replaced my username in the above by ${USER} for security reasons. It is there.)

Funny, I'm now noticing that this has a quote at the end but not at the start. Maybe this is why the games aren't found. How did it get there?

$ grep PATH /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"

$ grep PATH .bashrc
# PATH
export PATH=.:${PATH}

The /home/${USER}/bin bit is not in these, strangely...
Where else does the PATH variable usually get altered?

Anyway, this is one I can fix myself and may be unrelated, so back to the adept problem:
Can anyone reproduce this problem / has had it before?

Cheers,
drushka

System:
Kubuntu DVD on a Lenovo Thinkpad T60 KDE 3.5.5, no XGL, no beryl or such installed.
Up to date as of this morning CET (using aptitude update / aptitude -f dist-upgrade) with the following sources.list:

$ cat /etc/apt/sources.list
## Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

## Proposed Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## Backports (new software versions, provided by the Ubuntu Backports Project)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## Commercial Software from Canonical
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main restricted universe multiverse

## PLF REPOSITORY
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free

## LISTEN
deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) dapper listen

## ntfs-3g
deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) edgy main-all

## Kubuntu Germany
deb [http://archive,kubuntu.de/ubuntu](http://archive,kubuntu.de/ubuntu) edgy main restricted universe multiverse il8n-de
deb-src [http://archive,kubuntu.de/ubuntu](http://archive,kubuntu.de/ubuntu) edgy main restricted universe multiverse il8n-de

## Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## Treviño's Ubuntu Repository
## (for Flash 9 Beta)
# deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy beryl-svn
# deb-src [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0

## swiftfox
deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

## Ubuntu Pouit Repository (v2) v6.10
## (for brasero)
#deb [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) edgy-pouit extra
#deb-src [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) edgy-pouit extra

## Latest Beryl and XGL
# deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main-edgy
# deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy
# deb-src [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy
deb [http://beryl-mirror.lupine.me.uk](http://beryl-mirror.lupine.me.uk) edgy all
deb-src [http://beryl-mirror.lupine.me.uk](http://beryl-mirror.lupine.me.uk) edgy all

# latest automatix2
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
#AUTOMATIX REPOS END

---

### Post by drushka on 2007-02-02
Hi all,

I've found the culprit, and the two problems actually ***were*** related.
The main problem actually affected kdesu, not adept. All calls of kdesu ended in "user no does not exist".

So to everyone who runs into the same problem, here's the solution.

I tried to find out what made the PATH string have a quotation mark at the end, and remembered that I'd edited the /etc/environment while browsing the web to build in some (unrelated) changes that I found on a webpage - under windows with the effect that it had ^M at the end of everey line.  ](*,) 
Removing those soved both of my problems. :guitar: 
Maybe it would be a good idea to make the parsers of configuration files robust against (admittedly stupid mistakes like) this?

Anyway, my /etc/environment is pretty short, only

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:
/usr/games"
LANG="en_US.UTF-8"

so it's still funny how either the PATH or the LANG variable could have affected kdesu in such a way.
Anyone know why that is?

Cheers,
drushka

---

