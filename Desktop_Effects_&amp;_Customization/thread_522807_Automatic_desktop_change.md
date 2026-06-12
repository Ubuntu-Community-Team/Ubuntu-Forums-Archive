---
title: "Automatic desktop change"
date: 2007-08-11
forum: Desktop Effects &amp; Customization
---

### Post by bmannering on 2007-08-11
I dont know if this is possible but i was wondering if there is an application or command that would change your wallpaper/desktop pic every time you log in.  any help or advice is great. Thanks

---

### Post by gjtoth on 2007-08-11
> **bmannering said:**
> I dont know if this is possible but i was wondering if there is an application or command that would change your wallpaper/desktop pic every time you log in.  any help or advice is great. Thanks

Desktop Drapes works just fine for me.

---

### Post by bmannering on 2007-08-11
thanks a lot it works great

---

### Post by sbubba on 2007-08-23
> **bmannering said:**
> thanks a lot it works great
Hello!
I've installed that program from the .deb, but it doesn't work :(  
this is the error on terminal:
```
speppa@sbubbo:~/drapes-0.4.97$ drapes

** (/usr/lib/drapes/drapes.exe:24851): WARNING **: The following assembly referenced from /usr/lib/drapes/drapes.exe could not be loaded:
     Assembly:   Mono.Posix    (assemblyref_index=5)
     Version:    2.0.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/drapes).


** (/usr/lib/drapes/drapes.exe:24851): WARNING **: Could not load file or assembly 'Mono.Posix, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

** (/usr/lib/drapes/drapes.exe:24851): WARNING **: Missing method Init in assembly /usr/lib/drapes/drapes.exe, type Mono.Unix.Catalog

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'Mono.Posix, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.
  at <0x00000> <unknown method>
  at Drapes.DrapesApp.Main (System.String[] args) [0x00000] 
```
so, I've tried to install it from the tar.gz, and this is the error after ./configure:
```
speppa@sbubbo:~/drapes-0.4.97$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.21... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... msgfmt
checking for msgmerge... msgmerge
checking for xgettext... xgettext
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for UNMANAGED_DEPENDENCIES_MONO... checking for UNMANAGED_DEPENDENCIES_MINT... configure: error: You need to install mono
```
I've installed mono from synaptic but nothing.. Do it need specific mono libraries? :confused:
(I've tried with 0.51, 0.50 and 4.9 version)
thanks [-o<

---

### Post by sbubba on 2007-08-24
I've solved that problem, but now I've another problem with make :|
with the version 0.4.97:

```
speppa@sbubbo:~/drapes-0.4.97$ make
Making all in drapes
make[1]: Entering directory `/home/speppa/drapes-0.4.97/drapes'
sed -e "s,[@]ASM_VERSION/[@],0.4.97.*,"         \
            -e "s,[@]datadir/[@],/usr/local/share,"                            \
                -e "s,[@]version/[@],0.4.97,"                           \
                -e "s,[@]helpdir/[@],/usr/local/share/gnome/help,"             \
            < AssemblyInfo.cs.in > AssemblyInfo.cs
/usr/bin/gmcs -debug  -r:System.Xml -r:Mono.Posix -pkg:gconf-sharp-2.0 -pkg:glade-sharp-2.0 -pkg:gnome-vfs-sharp-2.0 -resource:../data/drapes.glade,drapes.glade  \
        -unsafe+ -target:exe -out:"drapes.exe" \
        ./AssemblyInfo.cs ./panelapplet/*.cs ./Applet.cs ./AppletWidget.cs ./ConfigMenu.cs ./Main.cs ./Settings.cs ./Traylib.cs ./Wallpaper.cs ./WpList.cs
./ConfigMenu.cs(335,13): error CS0136: A local variable named `sender' cannot be declared in this scope because it would give a different meaning to `sender', which is already used in a `parent or current' scope to denote something else
./ConfigMenu.cs(285,41): (Location of the symbol related to previous error)
Compilation failed: 1 error(s), 0 warnings
make[1]: *** [drapes.exe] Error 1
make[1]: Leaving directory `/home/speppa/drapes-0.4.97/drapes'
make: *** [all-recursive] Error 1
```

and also with the version 0.5.0:
```
speppa@sbubbo:~/drapes-0.5.1$ make
Making all in drapes
make[1]: Entering directory `/home/speppa/drapes-0.5.1/drapes'
sed -e "s,[@]ASM_VERSION/[@],0.5.1.*,"          \
            -e "s,[@]datadir/[@],/usr/local/share,"                            \
                -e "s,[@]prefix/[@],/usr/local,"                               \
                -e "s,[@]version/[@],0.5.1,"                            \
                -e "s,[@]helpdir/[@],/usr/local/share/gnome/help,"             \
            < AssemblyInfo.cs.in > AssemblyInfo.cs
/usr/bin/gmcs -debug  -r:System.Xml -r:Mono.Posix -pkg:gconf-sharp-2.0 -pkg:glade-sharp-2.0 -pkg:gnome-vfs-sharp-2.0 -resource:../data/drapes.glade,drapes.glade  \
        -unsafe+ -target:exe -out:"drapes.exe" \
        ./AssemblyInfo.cs ./panelapplet/*.cs ./About.cs ./Applet.cs ./AppletWidget.cs ./ConfigMenuWidgets.cs ./ConfigMenu.cs ./Main.cs ./Settings.cs ./Traylib.cs ./Wallpaper.cs ./WpList.cs
./WpList.cs(86,27): warning CS0612: `Gnome.Vfs.Mime.TypeFromName(string)' is obsolete
./WpList.cs(474,36): warning CS0612: `Gnome.Vfs.Mime.TypeFromName(string)' is obsolete
./panelapplet/BonoboUIVerb.cs(14,10): warning CS0414: The private field `_Gnome.BonoboUIVerb.verb' is assigned but its value is never used
./panelapplet/BonoboUIVerb.cs(15,27): warning CS0414: The private field `_Gnome.BonoboUIVerb.callback' is assigned but its value is never used
./panelapplet/BonoboUIVerb.cs(16,10): warning CS0414: The private field `_Gnome.BonoboUIVerb.user_data' is assigned but its value is never used
./panelapplet/BonoboUIVerb.cs(17,10): warning CS0414: The private field `_Gnome.BonoboUIVerb.dummy' is assigned but its value is never used
./Applet.cs(83,22): warning CS0169: The private method `Drapes.DrapesApplet.ShowHelp()' is never used
./Traylib.cs(46,23): warning CS0414: The private field `Egg.TrayIcon.orientation' is assigned but its value is never used
./Wallpaper.cs(123,36): warning CS0169: The private field `Drapes.Wallpaper.style' is never used
Compilation succeeded - 9 warning(s)
make[1]: Leaving directory `/home/speppa/drapes-0.5.1/drapes'
Making all in scripts
make[1]: Entering directory `/home/speppa/drapes-0.5.1/scripts'
sed -e 's,[@]pkglibdir/[@],/usr/local/lib/drapes,'              \
                < drapes.in > drapes
chmod +x drapes
make[1]: Leaving directory `/home/speppa/drapes-0.5.1/scripts'
Making all in data
make[1]: Entering directory `/home/speppa/drapes-0.5.1/data'
Making all in images
make[2]: Entering directory `/home/speppa/drapes-0.5.1/data/images'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/speppa/drapes-0.5.1/data/images'
make[2]: Entering directory `/home/speppa/drapes-0.5.1/data'
LC_ALL=C ../intltool-merge -d -u -c ../po/.intltool-merge-cache ../po drapes.desktop.in drapes.desktop
Generating and caching the translation database
Merging translations into drapes.desktop.
LC_ALL=C ../intltool-merge -s -u -c ../po/.intltool-merge-cache ../po drapes.schemas.in drapes.schemas
Found cached translation database
Merging translations into drapes.schemas.
sed -e 's,[@]bindir/[@],/usr/local/bin,'       \
            < DrapesApplet.server.in.in > DrapesApplet.server.in
LC_ALL=C ../intltool-merge -o -u -c ../po/.intltool-merge-cache ../po DrapesApplet.server.in DrapesApplet.server
Found cached translation database
Merging translations into DrapesApplet.server.
make[2]: Leaving directory `/home/speppa/drapes-0.5.1/data'
make[1]: Leaving directory `/home/speppa/drapes-0.5.1/data'
Making all in help
make[1]: Entering directory `/home/speppa/drapes-0.5.1/help'
xsltproc -o drapes-C.omf --stringparam db2omf.basename drapes --stringparam db2omf.format 'docbook' --stringparam db2omf.dtd "-//OASIS//DTD DocBook XML V4.2//EN" --stringparam db2omf.lang C --stringparam db2omf.omf_dir "/usr/local/share/omf" --stringparam db2omf.help_dir "/usr/local/share/gnome/help" --stringparam db2omf.omf_in "/home/speppa/drapes-0.5.1/help/drapes.omf.in" --stringparam db2omf.scrollkeeper_cl "`scrollkeeper-config --pkgdatadir`/Templates/C/scrollkeeper_cl.xml" `/usr/bin/pkg-config --variable db2omf gnome-doc-utils` C/drapes.xml || { rm -f "drapes-C.omf"; exit 1; }
xsltproc -o drapes-fr.omf --stringparam db2omf.basename drapes --stringparam db2omf.format 'docbook' --stringparam db2omf.dtd "-//OASIS//DTD DocBook XML V4.2//EN" --stringparam db2omf.lang fr --stringparam db2omf.omf_dir "/usr/local/share/omf" --stringparam db2omf.help_dir "/usr/local/share/gnome/help" --stringparam db2omf.omf_in "/home/speppa/drapes-0.5.1/help/drapes.omf.in" --stringparam db2omf.scrollkeeper_cl "`scrollkeeper-config --pkgdatadir`/Templates/C/scrollkeeper_cl.xml" `/usr/bin/pkg-config --variable db2omf gnome-doc-utils` fr/drapes.xml || { rm -f "drapes-fr.omf"; exit 1; }
xsltproc -o drapes-it.omf --stringparam db2omf.basename drapes --stringparam db2omf.format 'docbook' --stringparam db2omf.dtd "-//OASIS//DTD DocBook XML V4.2//EN" --stringparam db2omf.lang it --stringparam db2omf.omf_dir "/usr/local/share/omf" --stringparam db2omf.help_dir "/usr/local/share/gnome/help" --stringparam db2omf.omf_in "/home/speppa/drapes-0.5.1/help/drapes.omf.in" --stringparam db2omf.scrollkeeper_cl "`scrollkeeper-config --pkgdatadir`/Templates/C/scrollkeeper_cl.xml" `/usr/bin/pkg-config --variable db2omf gnome-doc-utils` it/drapes.xml || { rm -f "drapes-it.omf"; exit 1; }
xsltproc -o drapes-ko.omf --stringparam db2omf.basename drapes --stringparam db2omf.format 'docbook' --stringparam db2omf.dtd "-//OASIS//DTD DocBook XML V4.2//EN" --stringparam db2omf.lang ko --stringparam db2omf.omf_dir "/usr/local/share/omf" --stringparam db2omf.help_dir "/usr/local/share/gnome/help" --stringparam db2omf.omf_in "/home/speppa/drapes-0.5.1/help/drapes.omf.in" --stringparam db2omf.scrollkeeper_cl "`scrollkeeper-config --pkgdatadir`/Templates/C/scrollkeeper_cl.xml" `/usr/bin/pkg-config --variable db2omf gnome-doc-utils` ko/drapes.xml || { rm -f "drapes-ko.omf"; exit 1; }
xsltproc -o drapes-pt.omf --stringparam db2omf.basename drapes --stringparam db2omf.format 'docbook' --stringparam db2omf.dtd "-//OASIS//DTD DocBook XML V4.2//EN" --stringparam db2omf.lang pt --stringparam db2omf.omf_dir "/usr/local/share/omf" --stringparam db2omf.help_dir "/usr/local/share/gnome/help" --stringparam db2omf.omf_in "/home/speppa/drapes-0.5.1/help/drapes.omf.in" --stringparam db2omf.scrollkeeper_cl "`scrollkeeper-config --pkgdatadir`/Templates/C/scrollkeeper_cl.xml" `/usr/bin/pkg-config --variable db2omf gnome-doc-utils` pt/drapes.xml || { rm -f "drapes-pt.omf"; exit 1; }
xsltproc -o drapes-pt_BR.omf --stringparam db2omf.basename drapes --stringparam db2omf.format 'docbook' --stringparam db2omf.dtd "-//OASIS//DTD DocBook XML V4.2//EN" --stringparam db2omf.lang pt_BR --stringparam db2omf.omf_dir "/usr/local/share/omf" --stringparam db2omf.help_dir "/usr/local/share/gnome/help" --stringparam db2omf.omf_in "/home/speppa/drapes-0.5.1/help/drapes.omf.in" --stringparam db2omf.scrollkeeper_cl "`scrollkeeper-config --pkgdatadir`/Templates/C/scrollkeeper_cl.xml" `/usr/bin/pkg-config --variable db2omf gnome-doc-utils` pt_BR/drapes.xml || { rm -f "drapes-pt_BR.omf"; exit 1; }
xsltproc -o drapes-sv.omf --stringparam db2omf.basename drapes --stringparam db2omf.format 'docbook' --stringparam db2omf.dtd "-//OASIS//DTD DocBook XML V4.2//EN" --stringparam db2omf.lang sv --stringparam db2omf.omf_dir "/usr/local/share/omf" --stringparam db2omf.help_dir "/usr/local/share/gnome/help" --stringparam db2omf.omf_in "/home/speppa/drapes-0.5.1/help/drapes.omf.in" --stringparam db2omf.scrollkeeper_cl "`scrollkeeper-config --pkgdatadir`/Templates/C/scrollkeeper_cl.xml" `/usr/bin/pkg-config --variable db2omf gnome-doc-utils` sv/drapes.xml || { rm -f "drapes-sv.omf"; exit 1; }
make[1]: Leaving directory `/home/speppa/drapes-0.5.1/help'
Making all in po
make[1]: Entering directory `/home/speppa/drapes-0.5.1/po'
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file de.po
/bin/sh: line 1: -o: command not found
make[1]: *** [de.gmo] Error 127
make[1]: Leaving directory `/home/speppa/drapes-0.5.1/po'
make: *** [all-recursive] Error 1
```

do nobody help me, please..?

---

### Post by sbubba on 2007-08-24
I've solved with the deb 0.50, thanks =)

---

### Post by Sikarian on 2007-08-24
I prefer using wallpaper-tray

---

