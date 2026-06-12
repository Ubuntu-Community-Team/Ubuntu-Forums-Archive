---
title: "Need a command to know the size of an installed package"
date: 2009-05-24
forum: General Help
---

### Post by colau on 2009-05-24
Hi,
Is there any command to know the size of an installed package?

---

### Post by Girl™ on 2009-05-24
The following command will give you the uncompressed size of a package: *aptitude show $package*

---

### Post by colau on 2009-05-24
> **Girl™ said:**
> The following command will give you the uncompressed size of a package: *aptitude show $package*
Thanks.
What does it mean by *uncompressed size*?
And does this command show all the dependencies?
```

aptitude show abiword

```
```

Package: abiword
New: yes
State: installed
Automatically installed: yes
Version: 2.6.6-0ubuntu1
Priority: optional
Section: gnome
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 7995k
Depends: libaiksaurus-1.2-0c2a (>= 1.2.1+dev-0.12), libaiksaurusgtk-1.2-0c2a (>=
         1.2.1+dev-0.12), libart-2.0-2 (>= 2.3.18), libatk1.0-0 (>= 1.20.0),
         libc6 (>= 2.7), libcairo2 (>= 1.2.4), libenchant1c2a (>= 1.4.2),
         libexpat1 (>= 1.95.8), libfontconfig1 (>= 2.4.0), libfreetype6 (>=
         2.3.5), libfribidi0 (>= 0.10.9), libgcc1 (>= 1:4.1.1), libglade2-0 (>=
         1:2.6.1), libglib2.0-0 (>= 2.18.0), libgnomecanvas2-0 (>= 2.11.1),
         libgnomeprint2.2-0 (>= 2.17.0), libgnomeprintui2.2-0 (>= 2.17.0),
         libgsf-1-114 (>= 1.14.11), libgtk2.0-0 (>= 2.15.0), libice6 (>=
         1:1.0.0), libidn11 (>= 0.5.18), libjpeg62, libloudmouth1-0 (>=
         1.1.4-2), libncurses5 (>= 5.6+20071006-3), libots0, libpango1.0-0 (>=
         1.22.0), libpng12-0 (>= 1.2.13-4), libpopt0 (>= 1.14), libreadline5 (>=
         5.2), librsvg2-2 (>= 2.22.3), libsm6, libstdc++6 (>= 4.2.1),
         libwmf0.2-7 (>= 0.2.8.4), libwpd8c2a, libwpg-0.1-1, libwv-1.2-3 (>=
         1.2.4), libx11-6, libxft2 (> 2.1.1), libxml2 (>= 2.6.27), zlib1g (>=
         1:1.1.4), abiword-common (>= 2.6.6-0ubuntu1), gsfonts
Recommends: abiword-plugin-grammar, abiword-plugin-mathview, abiword-help,
            aspell-en | aspell-dictionary, poppler-utils
Suggests: abiword-plugin-goffice
Conflicts: abiword-gnome
Replaces: abiword-gnome
Provides: abiword-gnome
Description: efficient, featureful word processor with collaboration
 AbiWord is a full-featured, efficient word processing application. It is
 suitable for a wide variety of word processing tasks, and is extensible with a
 variety of plugins. 
 
 This package includes many of the available import/export plugins allowing
 AbiWord to interact with ODT, WordPerfect, and other formats.  It also includes
 tools plugins, offering live collaboration with AbiWord users on Linux and
 Windows (using TCP or Jabber/XMPP), web translation and dictionary support, and
 more. 
 
 Additional plugins that require significant amounts of extra software to
 function are in the various abiword-plugin-* packages.
Homepage: http://www.abisource.com/

```

---

### Post by colau on 2009-05-25
Also here:
[http://www.math-linux.com/spip.php?article80](http://www.math-linux.com/spip.php?article80)

---

