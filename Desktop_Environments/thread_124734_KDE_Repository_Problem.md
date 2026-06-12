---
title: "KDE Repository Problem"
date: 2006-02-02
forum: Desktop Environments
---

### Post by Limulus on 2006-02-02
Hi hi!

Now, I actually use Ubuntu, but I have kubuntu-desktop installed for the various apps (and so I can occasionally login with KDE).  In my sources.list file I have the entry:

```
deb http://kubuntu.org/packages/kde-latest/ breezy main
```

(the kde-latest directory resolves to the same as the newest version on their server, so it just switched from 3.5.0 to 3.5.1)

Now a curious thing happened; I can't install the kdeedu metapackage because some of its required files just aren't there.  For example, khangman.  I had a look at [http://kubuntu.org/packages/kde351/dists/breezy/main/binary-i386/Packages](http://kubuntu.org/packages/kde351/dists/breezy/main/binary-i386/Packages) and what's surprising is that the packages I can't get are there, but not for i386! (khangman is listed as being for amd64)

Obviously then I'm not the only one having this problem; does anyone know when it will be resolved?

---

### Post by Sokraates on 2006-02-02
Kdeedu is not included in the 3.5.1-repos. If you use the latest repos **only**, a lot of packages are no longer available. I now use both 3.5 and 3.5.1-repos and will have to wait if this causes troubles.

I installed 3.5.1 using only the latest repo; it installed zeroconf and screwed up my network. Had to remove the package to make everything work again.

---

### Post by magnusbb on 2006-02-02
Yes, kdeedu is included, but only for amd64 users. The i386 packages are missing.

---

### Post by Limulus on 2006-02-02
Sokraates: no, kdeedu is listed in 3.5.1 (and showing up in Synaptic as such).

From the packages file I linked in my first post:

```

Package: kdeedu
Priority: optional
Section: kde
Installed-Size: 68
Maintainer: Ben Burton <bab@debian.org>
Architecture: all
Version: 4:3.5.1-0ubuntu0breezy1
Depends: kalzium (>= 4:3.5.1-0ubuntu0breezy1), kbruch (>= 4:3.5.1-0ubuntu0breezy1), kdeedu-data (>= 4:3.5.1-0ubuntu0breezy1), keduca (>= 4:3.5.1-0ubuntu0breezy1), khangman (>= 4:3.5.1-0ubuntu0breezy1), kig (>= 4:3.5.1-0ubuntu0breezy1), kiten (>= 4:3.5.1-0ubuntu0breezy1), klatin (>= 4:3.5.1-0ubuntu0breezy1), klettres (>= 4:3.5.1-0ubuntu0breezy1), kanagram (>= 4:3.5.1-0ubuntu0breezy1), kmplot (>= 4:3.5.1-0ubuntu0breezy1), kpercentage (>= 4:3.5.1-0ubuntu0breezy1), kstars (>= 4:3.5.1-0ubuntu0breezy1), ktouch (>= 4:3.5.1-0ubuntu0breezy1), kturtle (>= 4:3.5.1-0ubuntu0breezy1), kverbos (>= 4:3.5.1-0ubuntu0breezy1), kvoctrain (>= 4:3.5.1-0ubuntu0breezy1), kwordquiz (>= 4:3.5.1-0ubuntu0breezy1)
Suggests: kdeedu-doc-html
Filename: pool-breezy/kdeedu/kdeedu_3.5.1-0ubuntu0breezy1_all.deb
Size: 18244
MD5sum: c4f05de21462caceaa92fc9371de8a5a
Description: educational apps from the official KDE release
 This is a collection of educational applications provided with the official
 release of KDE (the K Desktop Environment).

```

magnusbb: kdeedu is for all three Ubuntu architechtures; while almost none of its dependencies are available for i386, kdeedu-data is though *shrug* (Edit: kdeedu-data is for "all" architechtures too, so that's why its showing up...  Hopefully the missing packages will be uploaded soon)

---

### Post by Sokraates on 2006-02-03
I've updated my laptop, too, and once again kdeedu, kstars and some other apps have been removed. this time I used both 3.5 and 3.5.1 repos. The -data packages are still installed, though.

I thought KDE-devs removed those packages but obvioulsly they've not been uploaded to breezy yet.

---

### Post by Limulus on 2006-02-05
I just had a very brief chat with Riddell on #kubuntu-devel and he is aware of the (mysterious) absence of the KDE 3.5.1 i386 kdeedu packages and said "I'll try and make new ones tomorrow" :)

---

### Post by Limulus on 2006-02-07
Update: they're up now!  I just finished installing the packages I wanted :)

---

