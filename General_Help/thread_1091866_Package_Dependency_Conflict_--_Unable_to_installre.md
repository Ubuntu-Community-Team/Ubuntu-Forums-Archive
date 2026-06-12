---
title: "Package Dependency Conflict -- Unable to install/remove anything"
date: 2009-03-09
forum: General Help
---

### Post by TroyDowling on 2009-03-09
I had a hard time giving a title to this problem chiefly because I have never encountered anything like this before. I'm not new to Ubuntu, but I have never come across this problem before. To be frank, while I am decently competent in Linux and particularly Ubuntu, I am totally up the river on this problem.

It all started when I granted my sister's request that I install a worms clone game, [Hedgewars (link)](http://www.hedgewars.org/node), on a couple of the machines here at home. Long story short, when it came to my computer things went south. In order to compile the game from source, I needed to install some [prerequisite packages (link)]("http://www.hedgewars.org/faq.html#q1") first. Because the convenient command on that page didn't work, I just fired up Synaptic to save me some time. I marked the counterparts to all the listed dependencies and started the install.

```

Commit Log for Mon Mar  9 12:10:38 2009


Upgraded the following packages:
fp-compiler (2.2.0-dfsg1-9ubuntu1) to 2.2.2-8
fp-units-base (2.2.0-dfsg1-9ubuntu1) to 2.2.2-8
fp-units-misc (2.2.0-dfsg1-9ubuntu1) to 2.2.2-8
fp-units-rtl (2.2.0-dfsg1-9ubuntu1) to 2.2.2-8
libc6 (2.8~20080505-0ubuntu9) to 2.9-4
libc6-amd64 (2.8~20080505-0ubuntu9) to 2.9-4
libc6-dev (2.8~20080505-0ubuntu9) to 2.9-4
libc6-dev-amd64 (2.8~20080505-0ubuntu9) to 2.9-4
libc6-i686 (2.8~20080505-0ubuntu9) to 2.9-4
libcups2 (1.3.9-2ubuntu7) to 1.3.9-14+b1
libdca0 (0.0.5-0.1) to 0.0.5-2
libgnutls-dev (2.4.1-1ubuntu0.2) to 2.6.4-2
libgnutls26 (2.4.1-1ubuntu0.2) to 2.6.4-2
libmad0 (0.15.1b-3) to 0.15.1b-4
libmodplug0c2 (1:0.7-7) to 1:0.8.4-3
libogg0 (1.1.3-4build1) to 1.1.3-5
libqt4-dbus (4.4.3-0ubuntu1.2) to 4.4.3-2
libqt4-designer (4.4.3-0ubuntu1.2) to 4.4.3-2
libqt4-network (4.4.3-0ubuntu1.2) to 4.4.3-2
libqt4-opengl (4.4.3-0ubuntu1.2) to 4.4.3-2
libqt4-qt3support (4.4.3-0ubuntu1.2) to 4.4.3-2
libqt4-script (4.4.3-0ubuntu1.2) to 4.4.3-2
libqt4-sql (4.4.3-0ubuntu1.2) to 4.4.3-2
libqt4-sql-mysql (4.4.3-0ubuntu1.2) to 4.4.3-2
libqt4-svg (4.4.3-0ubuntu1.2) to 4.4.3-2
libqt4-webkit (4.4.3-0ubuntu1.2) to 4.4.3-2
libqt4-xml (4.4.3-0ubuntu1.2) to 4.4.3-2
libqtcore4 (4.4.3-0ubuntu1.2) to 4.4.3-2
libqtgui4 (4.4.3-0ubuntu1.2) to 4.4.3-2
libsdl-mixer1.2 (1.2.8-4) to 1.2.8-5
libsmpeg0 (0.4.5+cvs20030824-2) to 0.4.5+cvs20030824-2.2
libvorbis0a (1.2.0.dfsg-3.1) to 1.2.0.dfsg-4
libvorbisenc2 (1.2.0.dfsg-3.1) to 1.2.0.dfsg-4
libvorbisfile3 (1.2.0.dfsg-3.1) to 1.2.0.dfsg-4
qt4-qtconfig (4.4.3-0ubuntu1.2) to 4.4.3-2

Installed the following packages:
cmake (2.6.3-2)
cmake-data (2.6.3-2)
cmake-gui (2.6.2-1ubuntu1~intrepid1)
emacsen-common (1.4.17)
fp-docs (2.2.2-8)
fp-units-db (2.2.2-8)
fp-units-fcl (2.2.2-8)
fp-units-fv (2.2.2-8)
fp-units-gfx (2.2.2-8)
fp-units-gnome1 (2.2.2-8)
fp-units-gtk (2.2.2-8)
fp-units-gtk2 (2.2.2-8)
fp-units-i386 (2.2.2-8)
fp-units-multimedia (2.2.2-8)
fp-units-net (2.2.2-8)
fp-utils (2.2.2-8)
liba52-0.7.4-dev (0.7.4-11ubuntu1)
libcups2-dev (1.3.9-14+b1)
libcupsys2-dev (1.3.9-14)
libdca-dev (0.0.5-2)
libdts-dev (0.0.5-2)
libgssapi-krb5-2 (1.6.dfsg.4~beta1-9)
libk5crypto3 (1.6.dfsg.4~beta1-9)
libkrb5-3 (1.6.dfsg.4~beta1-9)
libkrb5support0 (1.6.dfsg.4~beta1-9)
libmad0-dev (0.15.1b-4)
libmikmod2-dev (3.1.11-a-6ubuntu3)
libmodplug-dev (1:0.8.4-3)
libogg-dev (1.1.3-5)
libqt3-compat-headers (3:3.3.8-b-5ubuntu1)
libqt3-headers (3:3.3.8-b-5ubuntu1)
libqt3-mt-dev (3:3.3.8-b-5ubuntu1)
libqt4-assistant (4.4.3-2)
libqt4-dev (4.4.3-2)
libqt4-help (4.4.3-2)
libqt4-opengl-dev (4.4.3-2)
libqt4-sql-sqlite (4.4.3-2)
libqt4-test (4.4.3-2)
libqt4-xmlpatterns (4.4.3-2)
libsdl-mixer1.2-dev (1.2.8-5)
libsdl-net1.2-dev (1.2.7-2)
libsdl-ruby (1.3.1-1)
libsdl-ruby1.8 (1.3.1-1)
libsdl-sge (030809dfsg-2)
libsmpeg-dev (0.4.5+cvs20030824-2.2)
libvorbis-dev (1.2.0.dfsg-4)
libxmlrpc-c3 (1.06.27-1)
libxmu-dev (2:1.0.4-1)
libxmu-headers (2:1.0.4-1)
qt3-assistant (3:3.3.8-b-5ubuntu1)
qt3-designer (3:3.3.8-b-5ubuntu1)
qt3-dev-tools (3:3.3.8-b-5ubuntu1)
qt3-doc (3:3.3.8-b-5ubuntu1)
qt4-designer (4.4.3-2)
qt4-dev-tools (4.4.3-2)
qt4-doc (4.4.3-2)
qt4-qmake (4.4.3-2)

```
* Worth noting that I DO NOT have an AMD core. Yet it has selected libc6-amd64 and libc6-dev-amd64

Among the to-be packages, was one called "libc6" and as in the log, it seems Ubuntu upgraded it from its own version, to a stock version of higher level. This is pretty much where I lose my clue. The install failed with this error:

```

Unpacking replacement libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.9-4_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/localedef.1.gz', which is also in package belocs-locales-bin
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.9-4_i386.deb

```

Now I seem to be in some state of limbo where nothing is the right version. If I run an `aptitude update/upgrade` I get errors telling me that libc6 has unresolvable dependencies. If I try and remove it to start fresh, I find out just how many things rely on libc6 itself. I cannot install or remove any packages without getting errors relating to the broken libc6 packages. On odd occasions when I do updates, it tells me I need to update, what seems like, every single package on my computer. I apologize if my problem isn't very clear. I'm having a hard time understanding what's gone wrong myself. I'll try and clarify anything needed. If I could get some help to resolve this I would be very happy.

Troy.

---

### Post by pyrofreek_9 on 2009-03-10
The problem basically seems to be that two packages are trying to own the same file, so you just need to get one of them to give it up. Try:

```
sudo dpkg-divert /usr/share/man/man1/localedef.1.gz
sudo dpkg -i /var/cache/apt/archives/libc6_2.9-4_i386.deb
sudo apt-get install -f
```

---

### Post by TroyDowling on 2009-03-11
That didn't solve anything unfortunately. I've been poking around the web and I've come across nothing that helps me at all. I've also got another thread over on ExpertsExchange that has gotten me nowhere. I have backups from a while ago (Acronis backups) so I'm trying now to restore some of the earlier revisions on files. At first I tried just replacing /var but that didn't work so now I'm stepping it up with /var, /etc, /usr, /lib, /bin, and /root. Hopefully this'll work... Feels like I'm kind of Frankensteining my machine though. =) I took another backup (of the untampered, broken state) before if I need to fall back. I'll let you know how this goes. *fingers crossed*

In the mean time, do you mind explaining what exactly is the problem and how I can prevent it from happening again? I understand that two packages are staking claim to the same file, but why is this a problem and what can I do to stop it from happening again?

Thanks,
Troy.

---

### Post by MaxIBoy on 2009-03-11
Obviously, you can't remove libc6-- that's the GNU C library, and no C program for Linux will run without it installed. (Or maybe they'll run but they won't compile. I don't care to find out.)

The other package, belocs-locales-bin or whatever, has got to go. If apt doesn't want to allow you to uninstall it, use dpkg --purge instead.

---

### Post by TroyDowling on 2009-03-11
Ah, that would have been a good thing to try. I should have thought of that. Anyways, I've decided to just fall back a month to my earlier backup. I didn't really lose any work since that is mirrored around so all I lost was programs I had installed over that time and my settings. Nothing a good afternoon can't replace.

I suppose that puts an end to my problem, but I'd still like to know how this happened. Can any one give me a breakdown of what went wrong? Like I said, I guess I have zero experience dealing with package conflicts... aptitude has always pulled through for me.

---

### Post by mario.almeida on 2009-03-22
> **TroyDowling said:**
> Ah, that would have been a good thing to try. I should have thought of that. Anyways, I've decided to just fall back a month to my earlier backup. I didn't really lose any work since that is mirrored around so all I lost was programs I had installed over that time and my settings. Nothing a good afternoon can't replace.

I suppose that puts an end to my problem, but I'd still like to know how this happened. Can any one give me a breakdown of what went wrong? Like I said, I guess I have zero experience dealing with package conflicts... aptitude has always pulled through for me.

Same problem here.

tried..

sudo apt-get purge belocs-locales-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.9-4) but 2.8~20080505-0ubuntu9 is to be installed
  locales: Depends: belocs-locales-bin (>= 2.4-2.2ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


sudo dpkg --purge belocs-locales-bin
dpkg: dependency problems prevent removal of belocs-locales-bin:
 locales depends on belocs-locales-bin (>= 2.4-2.2ubuntu2).
dpkg: error processing belocs-locales-bin (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 belocs-locales-bin



Regards,
Remy

---

### Post by mc4man on 2009-03-22
@TroyDowling
If as you posted, synaptic was 'willing' to do those updates then you must have some jaunty (9.04)and possibly a debian repo source(s) enabled.
Mixing those with intrepid sources on an 8.10 install would eventually lead to the problems you posted. (if as it appears you have 8.10

@mario.almeida

You haven't given any context as to why your trying to purge belocs-locales-bin. (there isn't really any 'normal'  reason to do so
Are you trying to install something?

You should take a look in your sources list
```
cat /etc/apt/sources.list
```

Did you force an install or download and install a package(s) from somewhere other than intrepid repos lately?

---

### Post by mario.almeida on 2009-03-22
> **mc4man said:**
> @TroyDowling
If as you posted, synaptic was 'willing' to do those updates then you must have some jaunty (9.04)and possibly a debian repo source(s) enabled.
Mixing those with intrepid sources on an 8.10 install would eventually lead to the problems you posted. (if as it appears you have 8.10

@mario.almeida

You haven't given any context as to why your trying to purge belocs-locales-bin. (there isn't really any 'normal'  reason to do so
Are you trying to install something?

You should take a look in your sources list
```
cat /etc/apt/sources.list
```

Did you force an install or download and install a package(s) from somewhere other than intrepid repos lately?


Thanks.
I had added deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) sid main to sources.list wanted to install a package but I cant remember, uncommented it and was able to run update thanks.

Regards,
Remy

---

### Post by TroyDowling on 2009-03-24
> **mc4man said:**
> @TroyDowling
If as you posted, synaptic was 'willing' to do those updates then you must have some jaunty (9.04)and possibly a debian repo source(s) enabled.
Mixing those with intrepid sources on an 8.10 install would eventually lead to the problems you posted. (if as it appears you have 8.10

Aha! Therein lies the problem. You are correct; I had an old Debian repository enabled. I was using it for a few packages a couple months ago. I forgot to remove it from my sources and whadya know... it definitely came back to bite me. Thanks a tonne for the support, it's appreciated. I'll remember to be more careful with my sources.

Troy.

---

