---
title: "How to create my own personal repository?"
date: 2006-09-11
forum: Desktop Environments
---

### Post by vbgunz on 2006-09-11
I hope this isn't a lame question. When I first install Ubuntu I apt-get update/upgrade/customize. When I mention customize, I mean I download a whole bunch of applications outside the Ubuntu core. How can I download these applications (.debs), burn them onto a CD and then use that CD as my own personal repository?

In other words. Instead of enabling multiverse, universe, etc. I would like to enable my CD with the applications and then go about installing them from the CD without having to get them from the web. Also, if possible and if this applies, how do I say if an application exist *both* on the CD and over the web *prefer* to get it from the CD *if* the versions are the same?

The reason I ask is because I remember once trying just to download some stuff from apt *but* in the end I could not find them anywhere on the system :( Also, I am sure there is probably a format to the whole repository thing in which I am unfamiliar with. Can someone please help me out and write some pointers on how to download these apps and make my own personal repository?

Thank you!

---

### Post by vbgunz on 2006-09-14
*bump*

---

### Post by wkulecz on 2006-09-14
IF you find the answer please let me know.  

On RedHat/Fedora/Mandrake after getting the rpms on CD, USB drive, or whatever, all I had to do was as root: "cd /wherever/I/put/Them" and then do: "rpm -Uvh *.rpm" and bingo the new system has everything at the same version as the original I so tediously set up.  Still had to manually move over any config files I'd edited but for me that's just for X and samba.

apt downloads the *.deb files to /var/cache/apt/archives and by default doesn't delete them so you should still find the ones you've downloaded there.  I've no idea how to do anything with them other than with dpkg which is tedious and doesn't seem to accept wildcards -- good luck typing 100+ *.deb filenames correctly!

Sure I could write a script to do each file independently, but clearly I'd be re-inventing the wheel as synaptic clearly does what I want after it downloads the files, and I'd have to learn a bunch of crap about apt/dpkg etc. that I shouldn't have to care about!

--wally.

---

### Post by jimcooncat on 2006-09-14
I haven't had time to play with any of this stuff myself, but I've done some digging on the subject.

Dennis Kaarsemaker hosts a repository, and has a tool called Falcon he uses to maintain it. Sounds like what you're looking for!

Falcon is a tool that generates the repository meta-information (such as
package listings and release files) in order to transform a set of packages
into a proper repository.

Features
* Every subdir of the pool is automatically a component
* Easy to use 'all' metacomponent that contains all packages in all components
* Support for automatically signing the Release file
* Easy template based HTML output for repository indices
* Support for moving all old versions of sources and debs to a morgue dir
* Easy support for complete and partial mirrors
* Support for multiple releases and architectures
* Easy creation of .iso files
* Easy import of sources from other debian repositories

[http://seveas.ubuntulinux.nl/dists/dapper-seveas/extras/]("http://seveas.ubuntulinux.nl/dists/dapper-seveas/extras/")

For making packages, I've been told that CheckInstall is the way to go.
[http://asic-linux.com.mx/~izto/checkinstall/]("http://asic-linux.com.mx/~izto/checkinstall/")

You also might want to read this thread on meta-packages.
[http://www.ubuntuforums.org/showthread.php?t=69241]("http://www.ubuntuforums.org/showthread.php?t=69241")

---

### Post by wkulecz on 2006-09-14
I found this:  [http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-cdrom](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-cdrom)

listing the commands to add a CDROM to the apt.sources list.  Still unclear what rigormarole to go thru to make a "valid Debian CD"

My guess is if we can figure how how to make our CD of *.deb files into a "valid Debian CD" we could make snyaptic show only the files in our "CD repository" and choose "Mark all" and then let it install them with "apply".

HTH,
--wally.

---

### Post by vbgunz on 2006-09-16
many many thanks fellas! I've decided to look into it.

I got 483 packages. The final size is 492MB. This includes all packages to update my 6.06 installation along with all customized applications and all dependencies. I reinstalled 6.06 and got everything I needed and found them where wkulecz said they would be. Thanks :)

jimcooncat, I didn't exactly look into Falcon because I thought it was too big for what I wanted which was something very simple. In my mind, I only wanted to place all debs flat in a directory and simply be able to point to it as a repo and use it. Thank for the link jimcooncat :D

What I ultimately settled on doing was this and it works like a charm:

```
sudo apt-get install dpkg-dev
cd /var/cache/apt/archives
dpkg-scanpackages . /dev/null > Packages
```

The dpkg-scanpackages step really does require Packages to be upper cased... To test the repo I copied the archives directory to an external FAT16 drive and then opened up /etc/apt/sources.list . I commented every repo out and added my repo to the top in this format.

```
deb file:/fat16drivepath/archives ./
```

You really cannot forget the ./ on the end of that line. It's pretty simple. It's prefixed with 'deb' followed by the path to the deb directory and you suffix it with './'. voila, really pretty simple.

I reloaded Synaptic to check and make sure that my repo actually got picked up and it was indeed the only repo available. perfect! I restored sources.list back to it's original state, updated Synaptic and all was successful!

wkulecz, I looked at the link you provided. I haven't had a chance to look into the CD yet cause my drive is locked down *but* at this point cannot imagine it being even a little difficult to get working. In case I do end up in some trouble though, I've bookmarked it for the occassion :)

btw, my repo setup is 'trivial' as according to this page which helped a lot: [http://www.debian.org/doc/manuals/repository-howto/repository-howto](http://www.debian.org/doc/manuals/repository-howto/repository-howto)

Thanks fellas! I really appreciate your time and advice :)

---

### Post by vbgunz on 2006-11-08
I remember when I asked this question... Something reminded me of it too and I thought I share it with you guys and those who use the search tool :)

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) is a project that helps you create your own repository of the applications you download and update after installing Ubuntu for the first time. I don't know much about it and haven't used it yet but I thought I share the find here.

Have fun!

---

