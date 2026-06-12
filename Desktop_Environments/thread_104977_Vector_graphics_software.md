---
title: "Vector graphics software"
date: 2005-12-17
forum: Desktop Environments
---

### Post by Luuraja on 2005-12-17
Rather new in Linux and trying to move away from Windows.l
Is there any vector graphics soft than Inkscape?

---

### Post by Gustav on 2005-12-17
You could try scribus:
```
$ apt-cache show scribus
Package: scribus
Priority: optional
Section: graphics
Installed-Size: 14764
Maintainer: Oleksandr Moskalenko <malex@tagancha.org>
Architecture: i386
Version: 1.2.2.1-1ubuntu1
Replaces: scribus-doc-de, scribus-doc-en, scribus-doc-fr, scribus-template (<= 1.2.0.final+cvs20041227-1)
Depends: libart-2.0-2 (>= 2.3.16), libaudio2, libc6 (>= 2.3.4-1), libcupsys2-gnutls10 (>= 1.1.23-1), libfontconfig1 (>= 2.3.0), libfreetype6 (>= 2.1.5-1), libgcc1 (>= 1:4.0.0-7), libice6, libjpeg62, liblcms1 (>= 1.08-1), libpng12-0 (>= 1.2.8rel), libqt3-mt (>= 3:3.3.4), libsm6, libstdc++6 (>= 4.0.0-10), libtiff4, libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxft2 (>> 2.1.1), libxi6 | xlibs (>> 4.1.0), libxinerama1, libxml2 (>= 2.6.17), libxrandr2 | xlibs (>> 4.3.0), libxrender1, libxt6 | xlibs (>> 4.1.0), python2.4 (>= 2.3.90), zlib1g (>= 1:1.2.1), gs-gpl (>= 8.01) | gs-afpl (>= 8.14) | gs-esp (>= 7.07), python-tk
Recommends: xfonts-scalable | gsfonts-x11
Suggests: scribus-template, scribus-doc, ttf-bitstream-vera
Filename: pool/main/s/scribus/scribus_1.2.2.1-1ubuntu1_i386.deb
Size: 4947346
MD5sum: 445fca5c128557c9130e2e7f54c1f1ac
Description: Open Source Desktop Publishing
 .
 Scribus is an open source desktop page layout program with the aim of
 producing commercial grade output in PDF and Postscript, primarily, though
 not exclusively for Linux.
 .
 Scribus can be used for many tasks; from brochure design to newspapers,
 magazines, newsletters and posters to technical documentation. It has
 sophisticated page layout features like precision placing and rotating of text
 and/or images on a page, manual kerning of type, bezier curves polygons,
 precision placement of objects, layering with RGB and CMYK custom colors. The
 Scribus document file format is XML-based. Unlike proprietary binary file
 formats, even damaged documents, can be recovered with a simple text editor.
 .
 Scribus supports professional DTP features, such as CMYK color and a
 color management system to soft proof images for high quality color printing,
 flexible PDF creation options, Encapsulated PostScript import/export and
 creation of 4 color separations, import of EPS/PS and SVG as native vector
 graphics, Unicode text including right to left scripts such as Arabic and
 Hebrew via freetype. Graphic formats which can be placed in Scribus as images
 include PDF, Encapsulated Post Script (eps), TIFF, JPEG, PNG and XPixMap(xpm),
 and any bitmap type supported by QT3.
 .
 Printing, PDF and SVG creation are done via custom driver libraries and
 plug-ins, giving Scribus inventive features: the abilities to include
 presentation effects with PDF output, fully scriptable interactive PDF
 forms, SVG vector file output. The internal printer drivers fully support
 Level 2 and Level 3/PDF 1.4 postscript features including transparency and
 font embedding.
 .
 When run from KDE, Drag and Drop, for example from desktop to the canvas,
 is enabled. There is easy to use drag and drop scrapbook for frequently
 used items such as text blocks, pictures and custom shaped frames.
 .
 Homepage: http://www.scribus.net/
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: edubuntu-desktop
```

---

### Post by Gustav on 2005-12-17
Or maybe sodipodi is more what you want
```
$ apt-cache show sodipodi
Package: sodipodi
Priority: optional
Section: universe/graphics
Installed-Size: 3572
Maintainer: Davide Puricelli (evo) <evo@debian.org>
Architecture: i386
Version: 0.34-0.1
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.7.2), libc6 (>= 2.3.2.ds1-4), libfontconfig1 (>= 2.2.1), libfreetype6 (>= 2.1.5-1), libglib2.0-0 (>= 2.4.6), libgtk2.0-0 (>= 2.4.4), libpango1.0-0 (>= 1.6.0b), libpng12-0 (>= 1.2.5.0-4), libpopt0 (>= 1.7), libxml2 (>= 2.6.11), zlib1g (>= 1:1.2.1)
Filename: pool/universe/s/sodipodi/sodipodi_0.34-0.1_i386.deb
Size: 988500
MD5sum: 94a8aacc9b2bdbc9aeb3b68b0f261b8d
Description: Vector based drawing program
 Sodipodi loads and saves a subset of SVG (Scalable Vector Graphics)
 format, a standard maintained by the WWW consortium.
 .
 Sodipodi user interface should be familiar from CorelDraw and similar
 drawing programs. There are rectangles, ellipses, text items, bitmap
 images and freehand curves.
 As an added bonus both vector and bitmap objects can have alpha
 transparency and can be arbitrarily transformed.
 .
 Sodipodi supports multiple opened files and multiple views per file.
 Graphics can be printed and exported to png bitmaps.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```

---

### Post by Gustav on 2005-12-17
Or maybe sketch?
```
$ apt-cache show sketch
Package: sketch
Priority: optional
Section: universe/graphics
Installed-Size: 6352
Maintainer: Gregor Hoffleit <flight@debian.org>
Architecture: i386
Version: 0.6.15-1ubuntu2
Depends: python2.4, python-tk, python-imaging, libc6 (>= 2.3.4-1), libx11-6, libxext6, tcl8.4 (>= 8.4.5), tk8.4 (>= 8.4.5)
Suggests: gsfonts-x11 (>= 0.12), python-xml, python-reportlab
Filename: pool/universe/s/sketch/sketch_0.6.15-1ubuntu2_i386.deb
Size: 1382968
MD5sum: 977330711633f5f2e41e4c2aa034e752
Description: Interactive vector drawing program for X11
 Sketch is an interactive vector drawing program, comparable to CorelDraw.
 It currently support drawing primitives like rectangles, ellipses, Bezier
 curves, bitmap and EPS images and text. All objects can be rotated, scaled
 and sheared. Primitives can have fill and line properties. A number of
 special effects like blend groups, text to Bezier and text along a path
 are provided. Sketch supports an unlimited undo history.
 Import of XFig, AI, WMF, CMX and SVG files. Exports to EPS, AI and SVG.
 Sketch is written in Python with an Tkinter GUI. User scripts can be
 written in Python.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```

---

### Post by Luuraja on 2005-12-22
Thanks, Gustav.

All of these described by you are not my cup of coffee.
I have a pile of designs done using Corel9 and Adobe Illustrator 11 and which I want to use in future.

Scribus is not my cup of coffee. Maybe I seem to you simple-minded but this one remebers me year 1997 when I tried todo my artistic impressions in M$ Powerpoint.

Sodipodi. I knew that this is app made in Estonia, my fellow-by-nation. So I am very excited. Synaptic found it easely.

---

