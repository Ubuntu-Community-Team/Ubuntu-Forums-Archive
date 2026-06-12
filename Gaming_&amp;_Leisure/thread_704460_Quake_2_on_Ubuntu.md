---
title: "Quake 2 on Ubuntu"
date: 2008-02-22
forum: Gaming &amp; Leisure
---

### Post by Dark Aspect on 2008-02-22
What is the best way to play Quake 2 on 64-bit Ubuntu?Quake 2 from the repositories does not work and clams to have security issues:confused::confused:

Heres the message: 

> ***** WARNING *****

   The networking part of Quake II (especially the server part) contains
   several unfixed security issues. Therefore, Quake II should not be
   used over untrusted networks (like the internet). The version
   included in Debian is intended only for local play.   

   See for an possibly non-exhaustive list of issues:
   [http://archives.neohapsis.com/archives/bugtraq/2004-10/0299.html](http://archives.neohapsis.com/archives/bugtraq/2004-10/0299.html)
   [http://www.r1ch.net/stuff/r1q2/](http://www.r1ch.net/stuff/r1q2/)
   [http://bugs.debian.org/280573](http://bugs.debian.org/280573)

*******************

Do you understand the security implications of continuing?
y
QuakeIIForge 0.3
using /home/administrator/.quake2/baseq2/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading oss sound output driver, ok
/dev/dsp: Input/output error
SNDDMA_Init: Could not mmap /dev/dsp.
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so")
No joysticks found
recursive shutdown
Error: Couldn't load pics/colormap.pcx]

:confused::confused::confused::confused::confused:

---

### Post by Brebs on 2008-02-22
See [quake 2 thread](http://ubuntuforums.org/showthread.php?t=684353).

Compile them, and pay close attention to the PKGBUILD scripts. They work on 64-bit.

---

### Post by bwang on 2008-02-22
Install quake2-data if you don't have it already:

sudo apt-get install quake2-data

Then: 

sudo dpkg-reconfigure quake2-data

and follow the on-screen instructions

---

### Post by Dark Aspect on 2008-02-22
> **Brebs said:**
> See [quake 2 thread](http://ubuntuforums.org/showthread.php?t=684353).

Compile them, and pay close attention to the PKGBUILD scripts. They work on 64-bit.

I am confused on how to install [This package]("http://aur.archlinux.org/packages.php?do_Details=1&ID=14057"),I am sorry I don't mean to sound like a noob but when you said compile I was thinking make file.I don't know how to use a svn or what the PKGBUILD file does:confused::confused:

---

### Post by Brebs on 2008-02-22
The PKGBUILD is just a bash script. It does 3 things:

1. Use subversion to download the qudos program (this is the best version to use, because it contains improvements since the last, out-of-date snapshot tarball).

2. Run "make" on the Makefile (specifying a few options)

3. Install the executable and its files & libraries.

---

### Post by Dark Aspect on 2008-02-25
> **Brebs said:**
> The PKGBUILD is just a bash script. It does 3 things:

1. Use subversion to download the qudos program (this is the best version to use, because it contains improvements since the last, out-of-date snapshot tarball).

2. Run "make" on the Makefile (specifying a few options)

3. Install the executable and its files & libraries.

Thanks I figured it out after some Googling.

---

### Post by noabody on 2008-07-17
In Ubuntu 8.04 LTS Hardy Heron I was finally able to build qudos from svn.

The Gentoo ebuild file like the pkgbuild was invaluable to determine dependencies:

[http://bugs.gentoo.org/attachment.cgi?id=117904](http://bugs.gentoo.org/attachment.cgi?id=117904)

# Copyright 1999-2007 Gentoo Foundation
# Distributed under the terms of the GNU General Public License v2
# $Header: $

inherit eutils flag-o-matic subversion toolchain-funcs games

MY_PN="quake2"

DESCRIPTION="Enhanced Quake 2 engine"
HOMEPAGE="http://qudos.quakedev.com/"
SRC_URI=""

# View at [http://svn.quakedev.com/viewvc.cgi/qudos/trunk/](http://svn.quakedev.com/viewvc.cgi/qudos/trunk/)
ESVN_REPO_URI="svn://svn.quakedev.com/${PN}/trunk"

LICENSE="GPL-2"
SLOT="0"
KEYWORDS="~amd64 ~x86"
IUSE="alsa audacious cdinstall debug dedicated demo dga ipv6 joystick mods opengl optimize-cflags qmax oss sdl textures"

UIDEPEND="alsa? ( media-libs/alsa-lib )
	audacious? ( media-sound/audacious )
	dga? ( x11-libs/libXxf86dga )
	sdl? ( media-libs/libsdl )
	media-libs/jpeg
	media-libs/libogg
	media-libs/libpng
	media-libs/libvorbis
	virtual/opengl
	virtual/glu
	x11-libs/libX11
	x11-libs/libXext
	x11-libs/libXxf86vm"
COMMON="opengl? ( ${UIDEPEND} )
	!opengl? ( sdl? ( ${UIDEPEND} ) )
	!opengl? ( !sdl? ( !dedicated? ( ${UIDEPEND} ) ) )"
DEPEND="${COMMON}
	x11-proto/xf86vidmodeproto"

However neither xmms or audacious would build because the proper dev packages were not available.  Audacious required an older version I eventually found at the ubuntu launchpad:
[https://launchpad.net/ubuntu/hardy/i386/audacious-dev/1.3.2-4](https://launchpad.net/ubuntu/hardy/i386/audacious-dev/1.3.2-4)  

Which in turn needed an older version of libaudacious5 (= 1.3.2-4).

Thankfully the xmms would build from the latest dev library at:
[https://launchpad.net/ubuntu/hardy/i386/xmms-dev/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms-dev/1:1.2.10+20070601-1build2)

The moral of the story is that building from sources is HARD and requires some patience and effort.  Typically when the build fails there is a useful error that points you in the right direction.  Use [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu), it is a fantastic resource along with [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for finding packages and the files/dependencies.

Haven't even tested it yet.  Just grateful that it built.

---

### Post by Brebs on 2008-07-18
> **noabody said:**
> neither xmms or audacious would build
Neither are needed. This is what "make ... WITH_XMMS=NO WITH_AUDACIOUS=NO" is for.

---

