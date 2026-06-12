---
title: "ZSNES and Gens/GS 64-bit binaries"
date: 2012-02-12
forum: Emulators
---

### Post by there.is.only.xul on 2012-02-12
I have created ZSNES and Gens/GS binaries for the 64-bit platform for the emulation of Super Nintendo / Super Game Boy and Sega Genesis / 32X / Sega CD.

All I did was modify... practically the entire control files for each package. Far as I know both are current and up-to-date. Gens/GS is understandable since it's been not updated since 2008. But ZSNES? You try installing it. It's there, yes, but still, go ahead and try, see what happens. Enough said.

ZSNES, modified from Debian Wheezy's available copy for AMD64:
[Mediafire [External link]]("http://www.mediafire.com/?f74okgtifb1ibmz")

Gens/GS, with an updated control file:
[Mediafire [External link]]("http://www.mediafire.com/?qy35yf8ppxh5m31")

For the future, when I am not around to maintain and upload possible updated versions, Build it yourself, or if someone made a 32-bit build, do the following:
1. Download the package into it's own folder
2. Open a terminal and navigate to said folder
3. [FONT=Courier New]dpkg-deb -x $TMP $PKG.deb[/FONT] ($TMP = Whatever you name it, $PKG = Package name)
4. [FONT=Courier New]dpkg-deb --control $PKG.deb[/FONT]
5. Edit control file in /DEBIAN ([FONT=Courier New]gedit DEBIAN/control[/FONT])
6. move DEBIAN into $TMP ([FONT=Courier New]mv DEBIAN $TMP[/FONT])
7. Back to terminal, [FONT=Courier New]dpkg -b $TMP $NEWPKG.deb[/FONT] ($NEWPKG = Whatever you name it.)

---

### Post by there.is.only.xul on 2012-02-13
If you know anybody that won't jump from Windows to Linux without any sort of emulation support, well now you have two reasons to with the binaries I have created. I know before there were some 64-bit users asking for ZSNES, and I provided something that would be 24/7 available.

Have fun, and if you can, +1 this thread so more people wanting ZSNES for 64-bit Ubuntu know about it! I wouldn't provide it if I didn't know it worked. :)

---

### Post by fubofo on 2012-04-29
+1

Also these forums REALLY need updated to include things like 'thanks' and so on

---

### Post by fubofo on 2012-04-29
Note: this Gens package depends of rar

Would it be possible to set 7-zip as an alternative as it also handles rar archives?

---

### Post by fubofo on 2012-04-29
OK so I can't get either of these two emulators to actually launch. Any help?

---

### Post by gerowen on 2013-02-10
> **there.is.only.xul said:**
> I have created ZSNES and Gens/GS binaries for the 64-bit platform for the emulation of Super Nintendo / Super Game Boy and Sega Genesis / 32X / Sega CD.

All I did was modify... practically the entire control files for each package. Far as I know both are current and up-to-date. Gens/GS is understandable since it's been not updated since 2008. But ZSNES? You try installing it. It's there, yes, but still, go ahead and try, see what happens. Enough said.

ZSNES, modified from Debian Wheezy's available copy for AMD64:
[Mediafire [External link]]("http://www.mediafire.com/?f74okgtifb1ibmz")

Gens/GS, with an updated control file:
[Mediafire [External link]]("http://www.mediafire.com/?qy35yf8ppxh5m31")

For the future, when I am not around to maintain and upload possible updated versions, Build it yourself, or if someone made a 32-bit build, do the following:
1. Download the package into it's own folder
2. Open a terminal and navigate to said folder
3. [FONT=Courier New]dpkg-deb -x $TMP $PKG.deb[/FONT] ($TMP = Whatever you name it, $PKG = Package name)
4. [FONT=Courier New]dpkg-deb --control $PKG.deb[/FONT]
5. Edit control file in /DEBIAN ([FONT=Courier New]gedit DEBIAN/control[/FONT])
6. move DEBIAN into $TMP ([FONT=Courier New]mv DEBIAN $TMP[/FONT])
7. Back to terminal, [FONT=Courier New]dpkg -b $TMP $NEWPKG.deb[/FONT] ($NEWPKG = Whatever you name it.)

Sorry to resurrect an old thread, but thanks for this.  I just downloaded and installed the 32 bit version on my Ubuntu 12.10 64 bit, and it kept yelling at me about broken dependencies, even though the emulator ran just fine, and the only way to get it to shut up was to remove the 32 bit package.  This one installed and worked just fine, :-)

---

