---
title: "MPlayer does not start with GUI"
date: 2006-06-11
forum: Desktop Environments
---

### Post by Timokl on 2006-06-11
Hi there,

after upgrading to Dapper, i cannot use Mplayer any more. Well, actually I can start it perfectly through a terminal window with the command:

```
mplayer /path/to/file
```

But when I try to start Mplayer through the Gnome menu, a window pops up and closes instantly.

Same goes if I try to start Mplayer through command line with:

```
gmplayer /path/to/file
```

Mplayer complains that Skins are missing, but they are installed.

I did install Mplayer through apt-get, I did not compile it by myself.

See also this thread for my problem: [http://ubuntuforums.org/showthread.php?t=193528](http://ubuntuforums.org/showthread.php?t=193528)

Any ideas what could be the problem?

Bye,
Timo

---

### Post by Anduu on 2006-06-11
I would try uninstalling making sure to remove any residual config and reinstalling.

---

### Post by Timokl on 2006-06-11
[QUOTE=Anduu]I would try uninstalling making sure to remove any residual config and reinstalling.[/QUOTE]

That's what I did just now. I removed everything Mplayer related with Synaptic. Then I updated my sources.list -- and Mplayer was gone from the repos!

```
timo@ubuntu:~$ sudo apt-get mplayer
E: Ungültige Operation mplayer.
timo@ubuntu:~$ sudo apt-get install mplayer
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut... Fertig
Paket mplayer ist nicht verfügbar, wird aber von einem anderen
Paket referenziert. Das kann heißen, dass das Paket fehlt, dass es veraltet
ist oder nur aus einer anderen Quelle verfügbar ist.
E: Paket mplayer hat keinen Installationskandidaten

```

Here's my sources.list

```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

## Cipherfunk multimedia packages (GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

```

---

### Post by Anduu on 2006-06-11
Hmmm that is strange...mplayer is in the multiverse repo.

Here is my sources.list for reference

```
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
```

---

### Post by Timokl on 2006-06-11
[QUOTE=Anduu]Hmmm that is strange...mplayer is in the multiverse repo.

Here is my sources.list for reference[/QUOTE]

I just tried your sources.list, then apt updating, and then apt-getting mplayer. But there is no installation candidate. :confused: 

However, I noticed one interesting thing concerning the repos:

```
gzip: stdin: not in gzip format
Fehl http://archive.ubuntu.com dapper/multiverse Packages
  Unterprozess gzip ist mit einem Fehlercode zurückgekehrt (1)
Es wurden 4928B in 12s geholt (379B/s)
Konnte http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz nicht holen  Unterprozess gzip ist mit einem Fehlercode zurückgekehrt (1)

```

I downloaded the repo list with my webbrowser and found, that it's not gzipped but an uncompressed text file. 

What do you mean: Is this the reason?

---

### Post by Anduu on 2006-06-11
:-k 

I don't know what to tell you...mplayer is in the repos when I check.

Open Synaptic and browse by sections.Go to Graphics (multiverse).It is in there...

---

### Post by sarhento_lobo on 2006-06-11
You could try pointing your sources.list to another mirror; i.e., de.archive.ubuntu.com and check using that.

---

### Post by Timokl on 2006-06-11
[QUOTE=sarhento_lobo]You could try pointing your sources.list to another mirror; i.e., de.archive.ubuntu.com and check using that.[/QUOTE]

Thanks. I used the de.archive.ubuntu.com repos - and it worked. :D 

Is there a list with the official repository server, mirror servers, and their geographical location? I look for one within Southeast Asia or Australia.

Bye,
Timo

---

