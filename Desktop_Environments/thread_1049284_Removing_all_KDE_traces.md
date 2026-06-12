---
title: "Removing all KDE traces"
date: 2009-01-24
forum: Desktop Environments
---

### Post by spongypants23 on 2009-01-24
Hiya everyone,

I'm wondering how to completely remove any and all traces of KDE from my computer, unless some things from KDE are absolutely necessary for GNOME, which I doubt.

I installed Amarok a while back, when that suddenly stopped working. So I got Banshee instead and find it to be much nicer.

So now I would like to remove any and all traces of the KDE environment from my computer, if possible.


Currently running:
Ubuntu Intrepid Ibex 8.10
GNOME 2.24.1

---

### Post by dje on 2009-01-24
try the instructions [here]("http://www.psychocats.net/ubuntu/puregnome") ;)

dje

---

### Post by spongypants23 on 2009-01-24
Ooo.. Did that, and now I've got a slight problem with what packages are being removed.

Here are the packages that apt-get wants to remove:
```
  apache2 apache2-mpm-prefork apache2-utils apache2.2-common audacity
  gstreamer0.10-plugins-bad imagemagick libapache2-mod-php5 libaprutil1
  libaudio2 libdbd-mysql-perl libfftw3-3 libflac++6 libgmyth0 libmodplug0c2
  libmpcdec3 libmysqlclient15off libofa0 libpq5 libqscintilla2-3 libqt4-dbus
  libqt4-network libqt4-opengl libqt4-ruby1.8 libqt4-script libqt4-sql
  libqt4-svg libqt4-webkit libqt4-xml libqtcore4 libqtgui4 libraptor1
  librasqal0 librdf0 libruby1.8 libsmokeqt4-2 libtunepimp5 libtunepimp5-mp3
  mencoder mysql-client-5.0 mysql-common mysql-server mysql-server-5.0
  openoffice.org openoffice.org-base openoffice.org-base-core
  openoffice.org-calc openoffice.org-core openoffice.org-draw
  openoffice.org-emailmerge openoffice.org-filter-binfilter
  openoffice.org-gnome openoffice.org-gtk openoffice.org-impress
  openoffice.org-math openoffice.org-officebean
  openoffice.org-report-builder-bin openoffice.org-writer
  openoffice.org-writer2latex php5-mcrypt php5-mysql phpmyadmin python-uno
  raptor-utils redland-utils ruby1.8 vlc vlc-dbg vlc-nox

```

My main concern are the OpenOffice, Apache, mysql, php (and various other web server stuff)... As well as codecs, and other things that look to be needed...

I don't think this is normal..? Can these packages be safely removed and then re-installed without any changes in configurations? (Excluding the KDE packages)

---

### Post by Lunx on 2009-01-26
> **spongypants23 said:**
> Hiya everyone,

I'm wondering how to completely remove any and all traces of KDE from my computer, unless some things from KDE are absolutely necessary for GNOME, which I doubt.

I installed Amarok a while back, when that suddenly stopped working. So I got Banshee instead and find it to be much nicer.

So now I would like to remove any and all traces of the KDE environment from my computer, if possible.


Currently running:
Ubuntu Intrepid Ibex 8.10
GNOME 2.24.1


I'm completely new to Linux and Ubuntu, just into third week of this brilliant experience away from that "other" OS, so forgive me if I'm missing something here. I take it you have all your stuff backed up somewhere? Wouldn't a fresh install be the quickest and most thorough way to get rid of it completely, then just import the things you want from your back-up as required? I'm currently in the process of getting files off external and into Ubuntu (and it's a lot less scary than I expected)

I once tried removing all traces of Adobe stuff from my (ex)XP installation, too lazy to do a fresh install (plus I like a challenge LOL). What a freakin' nightmare, worse than a rootkit infection to get rid of. Anyhow I gave up and ended up doing what I should have done in the first place, fresh install... It's that type of experience that saw me give up on proprietry software pretty much altogether, really gets to me that I pay these huge, faceless and souless corporations exorbitant amounts of money so they can take control of my system in the way they do

Sorry I can't offer much help, I actually came here to seek a similar answer to how much mixing of KDE and Gnome you can have before stuff starts breaking, I saw this thread and thought I'd 'ave a read, so I best be off to seek answer before this becomes a thread hijack

Good luck with it, I hope you post again later and let us all know how it went.

-----------------------------
Quick edit:

(Oopps, didn't read OP closely enough,web sever etc. I see my "solution" probably isn't one now)

---

### Post by gyffes on 2009-02-01
> **dje said:**
> try the instructions [here]("http://www.psychocats.net/ubuntu/puregnome") ;)

dje

I have to say, that's a fairly extreme solution to the problem of a few too many KDE apps in the Ibex install.

Isn't there a rather simpler, more straightforward way to remove KDE traces that won't blow away NON-KDE-specific apps?

---

