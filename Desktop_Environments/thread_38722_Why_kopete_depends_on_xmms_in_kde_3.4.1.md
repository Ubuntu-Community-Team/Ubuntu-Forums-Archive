---
title: "Why kopete depends on xmms in kde 3.4.1?"
date: 2005-06-01
forum: Desktop Environments
---

### Post by Runico on 2005-06-01
I don't use xmms and I would like not to have it installed, but in kde 3.4.1 packages kopete depends on xmms, but I don't see the point.

---

### Post by philipacamaniac on 2005-06-01
[QUOTE=Runico]I don't use xmms and I would like not to have it installed, but in kde 3.4.1 packages kopete depends on xmms, but I don't see the point.[/QUOTE]
 It is the case in KDE 3.4 also (I think), anyway, it is because the "Now Playing" plugin in Kopete depends on xmms, regardless of which music player you actually use to play the music. We had a discussion on this topic in #kubuntu, and the consensus was that the "Now Playing" plugin upstream needs to be reworked to use DCOP calls to the default media player.

---

### Post by Runico on 2005-06-01
[QUOTE=philipacamaniac]It is the case in KDE 3.4 also (I think), anyway, it is because the "Now Playing" plugin in Kopete depends on xmms, regardless of which music player you actually use to play the music. We had a discussion on this topic in #kubuntu, and the consensus was that the "Now Playing" plugin upstream needs to be reworked to use DCOP calls to the default media player.[/QUOTE]

In KDE 3.4 I have installed kopete without xmms. It doesn't depends on xmms:
Depends: kdelibs4 (>= 4:3.4.0), libart-2.0-2 (>= 2.3.16), libaudio2, libc6 (>= 2.3.2.ds1-4), libfontconfig1 (>= 2.2.1), libfreetype6 (>= 2.1.5-1), libgadu3 (>= 1:1.5), libgamin0, libgcc1 (>= 1:4.0-0pre6ubuntu4), libice6 | xlibs (>> 4.1.0), libidn11 (>= 0.5.2), libjpeg62, libpcre3 (>= 4.5), libpng12-0 (>= 1.2.8rel), libqt3c102-mt (>= 3:3.3.3), libsm6 | xlibs (>> 4.1.0), libstdc++5 (>= 1:3.3.4-1), libx11-6 | xlibs (>> 4.1.0), libxcursor1 (>> 1.1.2), libxext6 | xlibs (>> 4.1.0), libxft2 (>> 2.1.1), libxinerama1, libxml2 (>= 2.6.17), libxrandr2 | xlibs (>> 4.3.0), libxrender1, libxslt1.1 (>= 1.1.12), libxt6 | xlibs (>> 4.1.0), zlib1g (>= 1:1.2.1)

And now playing plugin works here without xmms.

I've installed kopete 3.4.1 without xmms:
aptitude download kopete
sudo dpkg -i --force-depends kopete_4%3a3.4.1-0ubuntu0hoary1_i386.deb

and now playing plugin works without xmms.

I think it would be better to put xmms in recommends or suggest

---

### Post by Runico on 2005-06-02
Sorry, forget what I say last, now playing doesn't work without xmms.

---

### Post by philipacamaniac on 2005-06-02
[QUOTE=Runico]Sorry, forget what I say last, now playing doesn't work without xmms.[/QUOTE]

I say they drop the "Now Playing" plugin completely until it can be reworked with DCOP

EDIT: Apparently, this was filed as a bug in Debian, and the issue was fixed. However, the Kubuntu KDE 3.4.1 packages seem to have reopened the issue. I'm trying to poke the devels on #kubuntu to see what's up, since we can't file a bug for the KDE 3.4.1 packages.

---

### Post by philipacamaniac on 2005-06-03
An update was just pushed out from kubuntu.org including a kopete 3.4.1-0ubuntu2, so this issue was probably re-fixed.

---

