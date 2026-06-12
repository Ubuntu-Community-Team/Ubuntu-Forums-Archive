---
title: "lierolibre: old-school earthworm action game"
date: 2012-04-27
forum: Gaming &amp; Leisure
---

### Post by Arand on 2012-04-27
EDIT:
Version 0.5 is out! Get it from [_[COLOR="Navy"]https://launchpad.net/lierolibre/+download[/COLOR]_](https://launchpad.net/lierolibre).

[img]http://i.imgur.com/Gh1El.png[/img]
[[img]http://i.imgur.com/VmKIJs.png[/img]](http://imgur.com/VmKIJ)     [[img]http://i.imgur.com/r0rPss.png[/img]](http://imgur.com/r0rPs)     [[img]http://i.imgur.com/IQ0ePs.png[/img]](http://imgur.com/IQ0eP)     [[img]http://i.imgur.com/u5lDLs.png[/img]](http://imgur.com/u5lDL)

Hi there,

I've been working on a project known as lierolibre for a while now, you can get hold of the latest version from:[_[COLOR="Navy"]https://launchpad.net/lierolibre[/COLOR]_](https://launchpad.net/lierolibre), there are also packages available for Ubuntu 11.10 and 12.04 in a PPA.

lierolibre is a direct fork from [_[COLOR="Navy"]Liero[/COLOR]_](http://liero.be) (formerly OpenLiero), which itself was a remake of LIERO.

Give it a try, report a bug or two, comments welcome! :)


The main changes done in lierolibre compared to Liero is:

1. Relicensing and replacement of non-free content:

The original LIERO was released under a non-free "freeware" license, have spoken to the original developer which has kindly agreed to relicense all content which was created by him under the WTFPL. Graphics and game variables are what ends up being used in lierolibre out of this content.

The sounds in LIERO/Liero, which came from Molez, which itself had borrowed some of them from proprietary games, have all been replaced with original sounds (WTFPL) created by "sea".

lierolibre can in addition to reading from LIERO.EXE read and write game vars to a plaintext file instead, and this is what comes shipped by default.

2. General adaptation to *nix

Added in lierolibre is a simple module to allow for $HOME and system content separation. For ease of installation there's autotools (though freetype jam still works for the compilation step).

3. Scripts to handle the game data

Finally, lierolibre also includes a bunch of scripts to handle the extraction and repacking of sound, graphics and levels for Liero. In order to make modification of these more accessible. It is still quite limited, for example the graphics uses raw 8bit pixel values, which are extracted to greyscale xpm files, although the palette used in the game itself differs, so if one wanted to do serious editing one would need to keep referencing the liero palette (available in liero.cfg). It is a resonable compromise for now though, and somewhat nicer than using a hex editor, as it were.

If you happen to create some content for lierolibre, or find something which has a free license and might fit, leave a comment, or report a feature request bug ;)

There's also quite a lot of changes behind the scenes, if you want the gory details, have a look in the git log, (gitorious repository is linked from Launchpad).

---

### Post by Arand on 2012-05-03
Version 0.3 is out! See original post for more info, and user-visible changes since 0.2

---

### Post by earthpigg on 2012-05-04
Possible to get a direct .deb download?

---

### Post by Arand on 2012-05-05
> **earthpigg said:**
> Possible to get a direct .deb download?

You can always download it directly from the PPA:
[https://launchpad.net/~arand/+archive/ppa/+packages](https://launchpad.net/~arand/+archive/ppa/+packages)
Clicking on the relevant source package and then downloading the "lierolibre" and "lierolibre-data" .deb file for your architecture.

I'm hesitant to do stand-alone .deb packages, since that's not really what .deb packages are intended for.

The source for the debian packaging is kept at [https://launchpad.net/~arand/+archive/ppa/+packages](https://launchpad.net/~arand/+archive/ppa/+packages) by the way (standard git-buildpackage layout), should be fairly simple to build .deb packages yourself:

```

sudo apt-get install git-buildpackage
git clone git://anonscm.debian.org/pkg-games/lierolibre.git lierolibre-debian
cd lierolibre-debian
git checkout upstream; git checkout pristine-tar; git checkout master
mk-build-deps
sudo dpkg -i lierolibre-build-deps*.deb
sudo apt-get install -f
git-buildpackage -us -uc

```

---

### Post by earthpigg on 2012-05-05
> **Arand said:**
> 
I'm hesitant to do stand-alone .deb packages, since that's not really what .deb packages are intended for.


Technically correct on every single level, and socially incorrect on every single level.

"Quickly download one file and run without mussing about with the terminal and other crap that I don't care about" is a *technically* incorrect social construct that is nonetheless *socially* correct.

Else, playdeb and similar would not exist and be popular. But they do, and there's a reason for that. Please reconsider; I'd like to give it a shot and play but honestly not so much that I want to deal with *yet another* random ppa mucking up my update announcements.

But: your project, you're the boss, do what you will. :)

---

### Post by Arand on 2012-05-05
> **earthpigg said:**
> Technically correct on every single level, and socially incorrect on every single level.

"Quickly download one file and run without mussing about with the terminal and other crap that I don't care about" is a *technically* incorrect social construct that is nonetheless *socially* correct.

Else, playdeb and similar would not exist and be popular. But they do, and there's a reason for that. Please reconsider; I'd like to give it a shot and play but honestly not so much that I want to deal with *yet another* random ppa mucking up my update announcements.

But: your project, you're the boss, do what you will. :)

I can agree somewhat on the convenience bit. User choices are still a necessity, though of course they could be made more obvious, using direct links to the PPA packages above for example:

**12.04 (Precise):**
[U][data package for both]("https://launchpad.net/~arand/+archive/ppa/+files/lierolibre-data_0.4-1%7Eppa1%7Eprecise1_all.deb")
[64bit game package]("https://launchpad.net/~arand/+archive/ppa/+files/lierolibre_0.4-1%7Eppa1%7Eprecise1_amd64.deb")
[32bit game package]("https://launchpad.net/~arand/+archive/ppa/+files/lierolibre_0.4-1%7Eppa1%7Eprecise1_i386.deb")
[/U]
**11.10 (Oneiric):**
[U][data package for both]("https://launchpad.net/~arand/+archive/ppa/+files/lierolibre-data_0.4-1%7Eppa1%7Eoneiric1_all.deb")
[64bit game package]("https://launchpad.net/~arand/+archive/ppa/+files/lierolibre_0.4-1%7Eppa1%7Eoneiric1_amd64.deb")
[32bit game package]("https://launchpad.net/~arand/+archive/ppa/+files/lierolibre_0.4-1%7Eppa1%7Eoneiric1_i386.deb")[/U]

---

### Post by Arand on 2012-06-12
Version 0.4 is out, get it from [https://launchpad.net/lierolibre/trunk/0.4/](https://launchpad.net/lierolibre/trunk/0.4/)
Changes:
* Fixed a bug where the EXE file path would not be set
* Updated CFG file with variable name corrections
+ New CFG files (v1) will be written with correct names
+ Old CFG files (v0) with incorrect names can still be loaded
* Added automatic upgrading of CFG file from v0 to v1
+ Only upgrades if loading from $HOME / settings dir
+ Creates a backup named *_backup_XXXXX
* First binary linux release
- Uses hard-coded run-time search path and an included set of libs
- Also includes source code for libs under LGPL
* Include library sources in windows package
- As required by LGPL (previously in a separate package)

---

### Post by Arand on 2012-11-16
Hi all,

I've just released lierolibre version 0.5.

This version is pretty much only a bugfix release, so be sure to check it out
if it happens to fix an itch of yours :)

Get the source from
[https://launchpad.net/lierolibre/trunk/](https://launchpad.net/lierolibre/trunk/) ... 0.5.tar.xz

For binary releases and other downloads see
[https://launchpad.net/lierolibre/+download](https://launchpad.net/lierolibre/+download)

Packages for Ubuntu are at
[https://launchpad.net/~arand/+archive/ppa](https://launchpad.net/~arand/+archive/ppa)


NEWS:
Version 0.5 - November 2012, by Martin Erik Werner
* Fixed packgfx and packlev scripts to work with newer ImageMagick
* Fixed the packsounds script so that it won't fail with non-english shell
* Removed unused fullscreen resolution extension menu options
* Fixed default keybind Right Alt not working on Linux
* Fixed extended controls being empty if loaded from non-extended LIERO.DAT
+ Closes: [http://code.google.com/p/liero/issues/detail?id=3](http://code.google.com/p/liero/issues/detail?id=3)
* Changed windows homedir name from "settings" to "user"
* Pre-packed LIERO.CHR and LIERO.SND are now included in the source release
* Enabled cross-compilation from Linux for Windows

---

