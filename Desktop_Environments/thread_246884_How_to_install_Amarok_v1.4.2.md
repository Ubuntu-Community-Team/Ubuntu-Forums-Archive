---
title: "How to install Amarok v1.4.2"
date: 2006-08-29
forum: Desktop Environments
---

### Post by snakyjake on 2006-08-29
I'd really like to install the most current version of Amarok (v1.4.2).  

I'm also fairly new to linux, so installing packages is quite different that what I'm used to with Windows.  So I have a few questions that I'm hoping that someone can set me straight on.

The Amarok website ([http://amarok.kde.org/](http://amarok.kde.org/)) says there's a new version.  I'm expecting that the package is somewhere for me to install.  I've searched the Synaptic Package Manager and cannot find any other version other than 1.3.9.  

I also tried to add sources from "backport" from the instructions at [http://amarok.kde.org/wiki/Debian](http://amarok.kde.org/wiki/Debian).  I'm not exactly sure what I'm doing at this point, but I added the lines to source.list, and then reloaded the packages from Synaptic, search, but still did not find 1.4.2.

What am I supposed to do to install Amarok v1.4.2?

By the way, I'm also using Xubuntu/xfce.

Thank you,

Jake

---

### Post by srunni on 2006-08-29
Well, the newest version of Amarok is not available in (K)(X)Ubuntu right now (through the official repos). Generally, program versions are frozen between releases. A good example of this is OOo, which is currently version 2.0.3, but Ubuntu runs 2.0.2. Anyway, back to your question. I guess you could compile from source for the install, but be prepared to run into problems with dependencies: it WILL NOT be fun tracking down all the dependent packages you need installed, but you're welcome to try. Another option is to find a unofficial repo that updates faster, but don't expect full compatibility.

---

### Post by max_dingemans on 2006-08-29
You could try adding the amarok-latest repository to your sources.list. I haven't checked in the last few weeks, but I remember it having at least amaroK 1.4.1.
```
# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/amarok-latest dapper main

# kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/amarok-latest dapper main
```

And if you were wondering, These lines came from the [Ubuntu Source List Generator]("http://www.ubuntulinux.nl/source-o-matic").

---

### Post by snakyjake on 2006-08-29
> **srunni said:**
> Generally, program versions are frozen between releases.

I'm curious on why?  Please forgive my questions of ignorance, but if I was going to create a software program and say it is "released", why would I not want to package my product for release for the popular Debian package managers?  I'm used to Windows applications where when someone says a program is released, you get an installation package (ie. setup.exe), and simply run the software from Windows.  It almost seems like software vendors "release" their software to the Linux package managers (ie. Debian and RPM).  It is then up to Debian, RPM, etc, to truly package the software for actual distribution.  

Kinda confusing to me.

---

### Post by kaptainlange on 2006-08-30
Well it all boils down to the fact that there are countless distributions of Linux.  The developers who make Amarok don't really have the time to package (and keep in mind there are different package systems for different distros) a binary release for each distro.

If they spent time doing that they'd have less time to put out new releases and concentrate on their code.  Now you will find some projects that do a little extra, like VLC player, and provide you with binary distributions tailored to different flavors of linux, but realize it is an extra effort for them to do so.

---

### Post by sultanoswing on 2006-08-30
> **snakyjake said:**
> I'm curious on why?


If you want a distro which is easy to use and a bit more 'cutting edge' you could do worse than Fedora Core, which I've also used and enjoyed (currently evaluating Ubuntu and enjoyin it too!).

We are well served in the Linux community.

Oh, and back on topic, amarok 1.4.1 (installed from [HERE](http://kubuntu.org/announcements/amarok-1.4.1.php) works just fine for me...but 1.4.2 didn't (no album covers displayed)

---

### Post by zerwas on 2006-08-31
You can now easily install Amarok 1.4.2:
[Installing it]("http://kubuntu.org/announcements/amarok-1.4.2.php")

---

### Post by Stephen Howard on 2006-08-31
Keep in mind that recent upgrades of Amarok have left the software unable to play .flac files.  I ended up having to downgrade.

If you don't store your music in .flac format then you won't have a problem.

---

### Post by Uncle Spellbinder on 2006-08-31
I just got an update notification for v1.4.2. Works great.

---

