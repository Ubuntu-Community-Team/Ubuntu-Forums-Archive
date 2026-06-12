---
title: "Freeciv &amp; SDL"
date: 2007-03-04
forum: Gaming &amp; Leisure
---

### Post by Tampio on 2007-03-04
So I downloaded freeciv 2.1.0 beta source, extracted it, and then did 
```
./configure --enable-client=sdl
```
it goes on for a while and in the end it says:
```
checking for IMG_Load in -lSDL_image... no
configure: error: specified client 'sdl' not configurable (SDL_image is needed (www.libsdl.org))
```
so then I try to install it with
```
sudo apt-get install libsdl-image1.2-dev
```
and results are:
```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl-image1.2-dev: Depends: libsdl1.2-dev (>= 1.2.2-3.3) but it is not going to be installed
E: Broken packages

```
and then:
```
sudo apt-get install libsdl1.2-dev
```
gives me:
```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Broken packages

```
and...
```
 sudo apt-get install libglu1-mesa-dev

```
gives me:
```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libglu1-mesa-dev: Depends: libglu1-mesa (= 6.4.1-0ubuntu8) but 6.5.1+cvs20060824 is to be installed
E: Broken packages

```

So I guess old version of libglu1-mesa is the reason for this problem? What needs to be done to fix this?

---

### Post by Tampio on 2007-03-04
Adding [these]("http://ubuntu.beryl-project.org/dists/dapper/main/") Beryl repositories solved the problem. 
Now there's a problem installing the game with checkinstall. I type ./configure, make, sudo checkinstall, and it gives me a lot of text which doesn't all fit to the terminal. What fits is below:

>  /usr/bin/install -c -m 644 'newzealand.ruleset' '/usr/local/share/freeciv/nation/ newzealand.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/newzeal and.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'nigerian.ruleset' '/usr/local/share/freeciv/nation/ni gerian.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/nigeria n.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'norwegian.ruleset' '/usr/local/share/freeciv/nation/n orwegian.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/norwegi an.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'ottoman.ruleset' '/usr/local/share/freeciv/nation/ott oman.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/ottoman .ruleset': No such file or directory
 /usr/bin/install -c -m 644 'papuan.ruleset' '/usr/local/share/freeciv/nation/papu an.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/papuan. ruleset': No such file or directory
 /usr/bin/install -c -m 644 'persian.ruleset' '/usr/local/share/freeciv/nation/per sian.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/persian .ruleset': No such file or directory
 /usr/bin/install -c -m 644 'phoenician.ruleset' '/usr/local/share/freeciv/nation/ phoenician.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/phoenic ian.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'polish.ruleset' '/usr/local/share/freeciv/nation/poli sh.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/polish. ruleset': No such file or directory
 /usr/bin/install -c -m 644 'portuguese.ruleset' '/usr/local/share/freeciv/nation/ portuguese.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/portugu ese.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'quebecois.ruleset' '/usr/local/share/freeciv/nation/q uebecois.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/quebeco is.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'romanian.ruleset' '/usr/local/share/freeciv/nation/ro manian.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/romania n.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'roman.ruleset' '/usr/local/share/freeciv/nation/roman .ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/roman.r uleset': No such file or directory
 /usr/bin/install -c -m 644 'russian.ruleset' '/usr/local/share/freeciv/nation/rus sian.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/russian .ruleset': No such file or directory
 /usr/bin/install -c -m 644 'ryukyuan.ruleset' '/usr/local/share/freeciv/nation/ry ukyuan.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/ryukyua n.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'sami.ruleset' '/usr/local/share/freeciv/nation/sami.r uleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/sami.ru leset': No such file or directory
 /usr/bin/install -c -m 644 'scottish.ruleset' '/usr/local/share/freeciv/nation/sc ottish.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/scottis h.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'serbian.ruleset' '/usr/local/share/freeciv/nation/ser bian.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/serbian .ruleset': No such file or directory
 /usr/bin/install -c -m 644 'silesian.ruleset' '/usr/local/share/freeciv/nation/si lesian.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/silesia n.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'singaporean.ruleset' '/usr/local/share/freeciv/nation /singaporean.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/singapo rean.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'sioux.ruleset' '/usr/local/share/freeciv/nation/sioux .ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/sioux.r uleset': No such file or directory
 /usr/bin/install -c -m 644 'slovakian.ruleset' '/usr/local/share/freeciv/nation/s lovakian.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/slovaki an.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'slovenian.ruleset' '/usr/local/share/freeciv/nation/s lovenian.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/sloveni an.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'southafrican.ruleset' '/usr/local/share/freeciv/natio n/southafrican.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/southaf rican.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'soviet.ruleset' '/usr/local/share/freeciv/nation/sovi et.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/soviet. ruleset': No such file or directory
 /usr/bin/install -c -m 644 'spanish.ruleset' '/usr/local/share/freeciv/nation/spa nish.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/spanish .ruleset': No such file or directory
 /usr/bin/install -c -m 644 'sudanese.ruleset' '/usr/local/share/freeciv/nation/su danese.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/sudanes e.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'sumerian.ruleset' '/usr/local/share/freeciv/nation/su merian.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/sumeria n.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'swazi.ruleset' '/usr/local/share/freeciv/nation/swazi .ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/swazi.r uleset': No such file or directory
 /usr/bin/install -c -m 644 'swedish.ruleset' '/usr/local/share/freeciv/nation/swe dish.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/swedish .ruleset': No such file or directory
 /usr/bin/install -c -m 644 'swiss.ruleset' '/usr/local/share/freeciv/nation/swiss .ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/swiss.r uleset': No such file or directory
 /usr/bin/install -c -m 644 'taiwanese.ruleset' '/usr/local/share/freeciv/nation/t aiwanese.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/taiwane se.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'texan.ruleset' '/usr/local/share/freeciv/nation/texan .ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/texan.r uleset': No such file or directory
 /usr/bin/install -c -m 644 'thai.ruleset' '/usr/local/share/freeciv/nation/thai.r uleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/thai.ru leset': No such file or directory
 /usr/bin/install -c -m 644 'tibetan.ruleset' '/usr/local/share/freeciv/nation/tib etan.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/tibetan .ruleset': No such file or directory
 /usr/bin/install -c -m 644 'tunisian.ruleset' '/usr/local/share/freeciv/nation/tu nisian.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/tunisia n.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'turk.ruleset' '/usr/local/share/freeciv/nation/turk.r uleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/turk.ru leset': No such file or directory
 /usr/bin/install -c -m 644 'ukrainian.ruleset' '/usr/local/share/freeciv/nation/u krainian.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/ukraini an.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'uyghur.ruleset' '/usr/local/share/freeciv/nation/uygh ur.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/uyghur. ruleset': No such file or directory
 /usr/bin/install -c -m 644 'venezuelan.ruleset' '/usr/local/share/freeciv/nation/ venezuelan.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/venezue lan.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'vietnamese.ruleset' '/usr/local/share/freeciv/nation/ vietnamese.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/vietnam ese.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'viking.ruleset' '/usr/local/share/freeciv/nation/viki ng.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/viking. ruleset': No such file or directory
 /usr/bin/install -c -m 644 'welsh.ruleset' '/usr/local/share/freeciv/nation/welsh .ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/welsh.r uleset': No such file or directory
 /usr/bin/install -c -m 644 'westphalian.ruleset' '/usr/local/share/freeciv/nation /westphalian.ruleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/westpha lian.ruleset': No such file or directory
 /usr/bin/install -c -m 644 'zulu.ruleset' '/usr/local/share/freeciv/nation/zulu.r uleset'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/nation/zulu.ru leset': No such file or directory
make[3]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/data/nation'
make[2]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/data/nation'
make[2]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/data'
make[3]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/data'
make[3]: Nothing to be done for `install-exec-am'.
test -z "" || mkdir -p -- ""
test -z "" || mkdir -p -- ""
test -z "/usr/local/share/pixmaps" || mkdir -p -- "/usr/local/share/pixmaps"
 /usr/bin/install -c -m 644 'freeciv-client.png' '/usr/local/share/pixmaps/freeciv -client.png'
/usr/bin/install: setting permissions for `/usr/local/share/pixmaps/freeciv-client .png': No such file or directory
test -z "/usr/local/share/freeciv" || mkdir -p -- "/usr/local/share/freeciv"
 /usr/bin/install -c -m 644 'civ1.serv' '/usr/local/share/freeciv/civ1.serv'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/civ1.serv': No  such file or directory
 /usr/bin/install -c -m 644 'civ2.serv' '/usr/local/share/freeciv/civ2.serv'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/civ2.serv': No  such file or directory
 /usr/bin/install -c -m 644 'default.serv' '/usr/local/share/freeciv/default.serv'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/default.serv':  No such file or directory
 /usr/bin/install -c -m 644 'amplio.tilespec' '/usr/local/share/freeciv/amplio.til espec'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/amplio.tilespe c': No such file or directory
 /usr/bin/install -c -m 644 'isophex.tilespec' '/usr/local/share/freeciv/isophex.t ilespec'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/isophex.tilesp ec': No such file or directory
 /usr/bin/install -c -m 644 'isotrident.tilespec' '/usr/local/share/freeciv/isotri dent.tilespec'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/isotrident.til espec': No such file or directory
 /usr/bin/install -c -m 644 'trident.tilespec' '/usr/local/share/freeciv/trident.t ilespec'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/trident.tilesp ec': No such file or directory
 /usr/bin/install -c -m 644 'stdsounds.soundspec' '/usr/local/share/freeciv/stdsou nds.soundspec'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/stdsounds.soun dspec': No such file or directory
 /usr/bin/install -c -m 644 'helpdata.txt' '/usr/local/share/freeciv/helpdata.txt'
/usr/bin/install: setting permissions for `/usr/local/share/freeciv/helpdata.txt':  No such file or directory
make[3]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/data'
make[2]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/data'
make[1]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/data'
Making install in intl
make[1]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/intl'
if test "freeciv" = "gettext" \
           && test '' = 'intl-compat.o'; then \
          /bin/sh `case "bootstrap/mkinstalldirs" in /*) echo "bootstrap/mkinstall dirs" ;; *) echo "../bootstrap/mkinstalldirs" ;; esac` /usr/local/lib /usr/local/i nclude; \
          /usr/bin/install -c -m 644 libintl.h /usr/local/include/libintl.h; \
          @LIBTOOL@ --mode=install \
            /usr/bin/install -c -m 644 libintl.a /usr/local/lib/libintl.a; \
        else \
          : ; \
        fi
if test 'no' = yes; then \
          /bin/sh `case "bootstrap/mkinstalldirs" in /*) echo "bootstrap/mkinstall dirs" ;; *) echo "../bootstrap/mkinstalldirs" ;; esac` /usr/local/lib; \
          temp=/usr/local/lib/t-charset.alias; \
          dest=/usr/local/lib/charset.alias; \
          if test -f /usr/local/lib/charset.alias; then \
            orig=/usr/local/lib/charset.alias; \
            sed -f ref-add.sed $orig > $temp; \
            /usr/bin/install -c -m 644 $temp $dest; \
            rm -f $temp; \
          else \
            if test yes = no; then \
              orig=charset.alias; \
              sed -f ref-add.sed $orig > $temp; \
              /usr/bin/install -c -m 644 $temp $dest; \
              rm -f $temp; \
            fi; \
          fi; \
          /bin/sh `case "bootstrap/mkinstalldirs" in /*) echo "bootstrap/mkinstall dirs" ;; *) echo "../bootstrap/mkinstalldirs" ;; esac` /usr/local/share/locale; \
          test -f /usr/local/share/locale/locale.alias \
            && orig=/usr/local/share/locale/locale.alias \
            || orig=./locale.alias; \
          temp=/usr/local/share/locale/t-locale.alias; \
          dest=/usr/local/share/locale/locale.alias; \
          sed -f ref-add.sed $orig > $temp; \
          /usr/bin/install -c -m 644 $temp $dest; \
          rm -f $temp; \
        else \
          : ; \
        fi
if test "freeciv" = "gettext"; then \
          /bin/sh `case "bootstrap/mkinstalldirs" in /*) echo "bootstrap/mkinstall dirs" ;; *) echo "../bootstrap/mkinstalldirs" ;; esac` /usr/local/share/gettext/in tl; \
          /usr/bin/install -c -m 644 VERSION /usr/local/share/gettext/intl/VERSION ; \
          /usr/bin/install -c -m 644 ChangeLog.inst /usr/local/share/gettext/intl/ ChangeLog; \
          dists="Makefile.in config.charset locale.alias ref-add.sin ref-del.sin g ettext.h gettextP.h hash-string.h libgnuintl.h libgettext.h loadinfo.h bindtextdom .c dcgettext.c dgettext.c gettext.c finddomain.c loadmsgcat.c localealias.c textdo main.c l10nflist.c explodename.c dcigettext.c dcngettext.c dngettext.c ngettext.c plural.y localcharset.c intl-compat.c"; \
          for file in $dists; do \
            /usr/bin/install -c -m 644 ./$file \
                            /usr/local/share/gettext/intl/$file; \
          done; \
          chmod a+x /usr/local/share/gettext/intl/config.charset; \
          dists="plural.c"; \
          for file in $dists; do \
            if test -f $file; then dir=.; else dir=.; fi; \
            /usr/bin/install -c -m 644 $dir/$file \
                            /usr/local/share/gettext/intl/$file; \
          done; \
          dists="xopen-msg.sed linux-msg.sed po2tbl.sed.in cat-compat.c"; \
          for file in $dists; do \
            rm -f /usr/local/share/gettext/intl/$file; \
          done; \
        else \
          : ; \
        fi
make[1]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/intl'
Making install in utility
make[1]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/utility'
Making install in ftwl
make[2]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/utility/ftwl'
make[3]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/utility/ftwl'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/utility/ftwl'
make[2]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/utility/ftwl'
make[2]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/utility'
make[3]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/utility'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/utility'
make[2]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/utility'
make[1]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/utility'
Making install in common
make[1]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/common'
make  install-recursive
make[2]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/common'
Making install in aicore
make[3]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/common/aicore'
make[4]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/common/aicore'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/common/aicore'
make[3]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/common/aicore'
make[3]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/common'
make[4]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/common'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/common'
make[3]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/common'
make[2]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/common'
make[1]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/common'
Making install in tests
make[1]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/tests'
make[2]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/tests'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/tests'
make[1]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/tests'
Making install in win32
make[1]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/win32'
make[2]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/win32'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/win32'
make[1]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/win32'
Making install in ai
make[1]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/ai'
make[2]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/ai'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/ai'
make[1]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/ai'
Making install in dependencies
make[1]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies'
Making install in lua
make[2]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/l ua'
Making install in src
make[3]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/l ua/src'
Making install in lib
make[4]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/l ua/src/lib'
make[5]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/l ua/src/lib'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/lu a/src/lib'
make[4]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/lu a/src/lib'
make[4]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/l ua/src'
make[5]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/l ua/src'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/lu a/src'
make[4]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/lu a/src'
make[3]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/lu a/src'
make[3]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/l ua'
make[4]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/l ua'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/lu a'
make[3]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/lu a'
make[2]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/lu a'
Making install in tolua
make[2]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/t olua'
make[3]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/t olua'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/to lua'
make[2]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies/to lua'
make[2]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies'
make[3]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies'
make[2]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies'
make[1]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/dependencies'
Making install in server
make[1]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/server'
Making install in generator
make[2]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/server/generat or'
make[3]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/server/generat or'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/server/generato r'
make[2]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/server/generato r'
Making install in scripting
make[2]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/server/scripti ng'
make[3]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/server/scripti ng'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/server/scriptin g'
make[2]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/server/scriptin g'
make[2]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/server'
make[3]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/server'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'civserver' '/usr/local/bin/civserver'
/usr/bin/install: setting permissions for `/usr/local/bin/civserver': No such file  or directory
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/server'
make[2]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/server'
make[1]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/server'
Making install in client
make[1]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/client'
Making install in gui-sdl
make[2]: Entering directory `/home/janne/sorsat/freeciv-2.1.0-beta3/client/gui-sdl '
if gcc -DHAVE_CONFIG_H -I. -I. -I../..  -I./.. -I./../include -I../../utility -I.. /../common -I../../common/aicore -I../../intl -I./../agents -I/usr/local/include/S DL -D_GNU_SOURCE=1 -D_REENTRANT -I/usr/include/freetype2 -Wall -Wpointer-arith -Wc ast-align -Wmissing-prototypes -Wmissing-declarations -DLOCALEDIR="\"/usr/local/sh are/locale\"" -DDEFAULT_DATA_PATH="\".:data:~/.freeciv:/usr/local/share/freeciv\""   -g -O2 -Wall -Wpointer-arith -Wcast-align -Wmissing-prototypes -Wmissing-declara tions -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -fsigned-char -MT grap hics.o -MD -MP -MF ".deps/graphics.Tpo" -c -o graphics.o graphics.c; \
        then mv -f ".deps/graphics.Tpo" ".deps/graphics.Po"; else rm -f ".deps/gra phics.Tpo"; exit 1; fi
In file included from /usr/local/include/SDL/SDL_syswm.h:28,
                 from graphics.c:31:
/usr/local/include/SDL/SDL_stdinc.h:81: error: redeclaration of enumerator ‘SDL_FA LSE’
/usr/include/SDL/SDL_types.h:38: error: previous definition of ‘SDL_FALSE’ was her e
/usr/local/include/SDL/SDL_stdinc.h:83: error: redeclaration of enumerator ‘SDL_TR UE’
/usr/include/SDL/SDL_types.h:40: error: previous definition of ‘SDL_TRUE’ was here
/usr/local/include/SDL/SDL_stdinc.h:83: error: conflicting types for ‘SDL_bool’
/usr/include/SDL/SDL_types.h:40: error: previous declaration of ‘SDL_bool’ was her e
/usr/local/include/SDL/SDL_stdinc.h:128: error: redeclaration of enumerator ‘DUMMY _ENUM_VALUE’
/usr/include/SDL/SDL_types.h:111: error: previous definition of ‘DUMMY_ENUM_VALUE’  was here
/usr/local/include/SDL/SDL_stdinc.h:128: error: conflicting types for ‘SDL_DUMMY_E NUM’
/usr/include/SDL/SDL_types.h:111: error: previous declaration of ‘SDL_DUMMY_ENUM’ was here
make[2]: *** [graphics.o] Error 1
make[2]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/client/gui-sdl'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/client'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


---

### Post by Perfect Storm on 2007-03-04
Use **sudo make install** instead. checkinstall is not fool-proof and there's alot of applications/libs that can't use it.

---

### Post by Tampio on 2007-03-04
Argh.. both make and make install give the same errors at the end:
> In file included from /usr/local/include/SDL/SDL_syswm.h:28,
                 from graphics.c:31:
/usr/local/include/SDL/SDL_stdinc.h:81: error: redeclaration of enumerator ‘SDL_FALSE’
/usr/include/SDL/SDL_types.h:38: error: previous definition of ‘SDL_FALSE’ was here
/usr/local/include/SDL/SDL_stdinc.h:83: error: redeclaration of enumerator ‘SDL_TRUE’/usr/include/SDL/SDL_types.h:40: error: previous definition of ‘SDL_TRUE’ was here
/usr/local/include/SDL/SDL_stdinc.h:83: error: conflicting types for ‘SDL_bool’
/usr/include/SDL/SDL_types.h:40: error: previous declaration of ‘SDL_bool’ was here
/usr/local/include/SDL/SDL_stdinc.h:128: error: redeclaration of enumerator ‘DUMMY_ENUM_VALUE’
/usr/include/SDL/SDL_types.h:111: error: previous definition of ‘DUMMY_ENUM_VALUE’ was here
/usr/local/include/SDL/SDL_stdinc.h:128: error: conflicting types for ‘SDL_DUMMY_ENUM’
/usr/include/SDL/SDL_types.h:111: error: previous declaration of ‘SDL_DUMMY_ENUM’ was here
make[2]: *** [graphics.o] Error 1
make[2]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/client/gui-sdl'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/janne/sorsat/freeciv-2.1.0-beta3/client'
make: *** [install-recursive] Error 1


---

### Post by Perfect Storm on 2007-03-04
Try;
```
make clean
```
and start all over. How's the complete ./configure output looks like?

---

### Post by Tampio on 2007-03-04
Make clean and doing it all again resulted in the same errors. 
./configure looked like this:
> checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for gawk... (cached) mawk
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for ar... ar
checking for uname... uname
checking for iconv... yes
checking for iconv declaration...
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for libcharset... no
checking for nl_langinfo and CODESET... yes
checking for strerror in -lcposix... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for off_t... yes
checking for size_t... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether we are using the GNU C Library 2.1 or newer... yes
checking argz.h usability... yes
checking argz.h presence... yes
checking for argz.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking nl_types.h usability... yes
checking nl_types.h presence... yes
checking for nl_types.h... yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking for feof_unlocked... yes
checking for fgets_unlocked... yes
checking for getcwd... yes
checking for getegid... yes
checking for geteuid... yes
checking for getgid... yes
checking for getuid... yes
checking for mempcpy... yes
checking for munmap... yes
checking for putenv... yes
checking for setenv... yes
checking for setlocale... yes
checking for stpcpy... yes
checking for strchr... yes
checking for strcasecmp... yes
checking for strdup... yes
checking for strtoul... yes
checking for tsearch... yes
checking for __argz_count... yes
checking for __argz_stringify... yes
checking for __argz_next... yes
checking for iconv... (cached) yes
checking for iconv declaration... (cached)
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for nl_langinfo and CODESET... (cached) yes
checking for LC_MESSAGES... yes
checking whether NLS is requested... yes
checking whether included gettext is requested... no
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for GNU gettext in libc... yes
checking for dcgettext... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for bison... no
checking for catalogs to be installed...  ar cs ca da de el en_GB es et fa fi fr he hu it ja lt nl nb no pl pt pt_BR ro ru sv uk zh_CN
checking for ngettext in -lc... yes
checking whether libc's ngettext works at runtime... yes
checking for GNU xgettext version >= 0.10.36... yes
checking for GNU msgfmt version >= 0.10.35... yes
checking for C99 variadic macros... yes
checking for C99 variable arrays... yes
checking for C99 initializers... yes
checking for stdint.h... (cached) yes
checking for C99 stdint.h... yes
checking for gzgets in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for gzip... /bin/gzip
checking for sdl-config... /usr/local/bin/sdl-config
checking for SDL - version >= 1.1.4... yes
checking for IMG_Load in -lSDL_image... yes
checking SDL/SDL_image.h usability... yes
checking SDL/SDL_image.h presence... yes
checking for SDL/SDL_image.h... yes
checking for freetype-config... /usr/bin/freetype-config
checking for FreeType - version >= 2.1.3... yes
checking for iconv... (cached) yes
checking for iconv declaration... (cached)
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for libcharset... (cached) no
checking for nl_langinfo and CODESET... (cached) yes
checking for connect in -lsocket... no
checking for gethostbyaddr in -lbind... no
checking for X... libraries /usr/X11R6/lib, headers
checking whether Xfuncproto was supplied... no, found:  FUNCPROTO=15 NARROWPROTO
checking for sdl-config... (cached) /usr/local/bin/sdl-config
checking for SDL - version >= 1.0.0... yes
checking SDL/SDL_mixer.h usability... no
checking SDL/SDL_mixer.h presence... no
checking for SDL/SDL_mixer.h... no
checking for Mix_OpenAudio in -lSDL_mixer... no
checking building SDL_mixer support... no, install SDL_mixer first: [http://www.libsdl.org/projects/SDL_mixer/index.html](http://www.libsdl.org/projects/SDL_mixer/index.html)
checking for GGZ library: libggz... no
checking for gethostbyaddr in -lbind... (cached) no
checking readline/readline.h usability... no
checking readline/readline.h presence... no
checking for readline/readline.h... no
configure: WARNING: Did not find readline header file.
Configuring server without readline support.
checking for pow... yes
checking for main in -lnls... no
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for sys/types.h... (cached) yes
checking for unistd.h... (cached) yes
checking sys/utsname.h usability... yes
checking sys/utsname.h presence... yes
checking for sys/utsname.h... yes
checking sys/file.h usability... yes
checking sys/file.h presence... yes
checking for sys/file.h... yes
checking for libintl.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking for strings.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking sys/signal.h usability... yes
checking sys/signal.h presence... yes
checking for sys/signal.h... yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/termio.h usability... no
checking sys/termio.h presence... no
checking for sys/termio.h... no
checking sys/uio.h usability... yes
checking sys/uio.h presence... yes
checking for sys/uio.h... yes
checking termios.h usability... yes
checking termios.h presence... yes
checking for termios.h... yes
checking for an ANSI C-conforming const... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for socklen_t... yes
checking return type of signal handlers... void
checking for pid_t... yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for working strcoll... yes
checking for vprintf... yes
checking for _doprnt... no
checking for working vsnprintf... yes
checking for fileno... yes
checking for ftime... yes
checking for gethostname... yes
checking for getpwuid... yes
checking for inet_aton... yes
checking for select... yes
checking for snooze... no
checking for strerror... yes
checking for strcasecmp... (cached) yes
checking for strncasecmp... yes
checking for strlcat... no
checking for strlcpy... no
checking for strstr... yes
checking for usleep... yes
checking for vsnprintf... yes
checking for uname... yes
checking for flock... yes
checking for gethostbyname... yes
checking for connect... yes
checking for bind... yes
checking for working gettimeofday... yes
checking for fdopen... yes
checking for fcntl... yes
checking for SIGPIPE... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating data/Makefile
config.status: creating data/civclient.dsc
config.status: creating data/civserver.dsc
config.status: creating data/civserver.room
config.status: creating data/amplio/Makefile
config.status: creating data/flags/Makefile
config.status: creating data/misc/Makefile
config.status: creating data/trident/Makefile
config.status: creating data/isophex/Makefile
config.status: creating data/isotrident/Makefile
config.status: creating data/stdsounds/Makefile
config.status: creating data/default/Makefile
config.status: creating data/civ1/Makefile
config.status: creating data/civ2/Makefile
config.status: creating data/scenario/Makefile
config.status: creating data/nation/Makefile
config.status: creating data/themes/Makefile
config.status: creating data/themes/gui-sdl/Makefile
config.status: creating data/themes/gui-sdl/human/Makefile
config.status: creating utility/Makefile
config.status: creating utility/ftwl/Makefile
config.status: creating dependencies/Makefile
config.status: creating dependencies/lua/Makefile
config.status: creating dependencies/tolua/Makefile
config.status: creating dependencies/lua/src/Makefile
config.status: creating dependencies/lua/src/lib/Makefile
config.status: creating common/Makefile
config.status: creating common/aicore/Makefile
config.status: creating ai/Makefile
config.status: creating tests/Makefile
config.status: creating win32/Makefile
config.status: creating client/Makefile
config.status: creating client/agents/Makefile
config.status: creating client/include/Makefile
config.status: creating client/gui-sdl/Makefile
config.status: creating client/gui-gtk-2.0/Makefile
config.status: creating client/gui-xaw/Makefile
config.status: creating client/gui-win32/Makefile
config.status: creating client/gui-ftwl/Makefile
config.status: creating client/gui-stub/Makefile
config.status: creating server/Makefile
config.status: creating server/generator/Makefile
config.status: creating server/scripting/Makefile
config.status: creating manual/Makefile
config.status: creating intl/Makefile
config.status: WARNING:  intl/Makefile.in seems to ignore the --datarootdir setting
config.status: creating po/Makefile.in
config.status: WARNING:  po/Makefile.in.in seems to ignore the --datarootdir setting
config.status: creating doc/Makefile
config.status: creating doc/man/Makefile
config.status: creating doc/de/Makefile
config.status: creating doc/fr/Makefile
config.status: creating doc/it/Makefile
config.status: creating doc/ja/Makefile
config.status: creating doc/nl/Makefile
config.status: creating doc/sv/Makefile
config.status: creating freeciv.spec
config.status: creating bootstrap/undep.sh
config.status: creating data/Freeciv
config.status: creating client/freeciv.desktop
config.status: creating civ
config.status: creating ser
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
config.status: executing fc_default-1 commands
extending po/Makefile
config.status: executing fc_default-2 commands
silencing po/Makefile
config.status: executing fc_default-4 commands
modifying po/Makefile add-comments/escape
config.status: executing fc_default-5 commands
config.status: executing default commands


---

### Post by Perfect Storm on 2007-03-04
> checking SDL/SDL_mixer.h usability... no
checking SDL/SDL_mixer.h presence... no
checking for SDL/SDL_mixer.h... no
checking for Mix_OpenAudio in -lSDL_mixer... no
checking building SDL_mixer support... no, install SDL_mixer first: [http://www.libsdl.org/projects/SDL_mixer/index.html](http://www.libsdl.org/projects/SDL_mixer/index.html)

> checking for X... libraries /usr/X11R6/lib, headers
checking whether Xfuncproto was supplied... no, found: FUNCPROTO=15 NARROWPROTO

> checking for GGZ library: libggz... no
checking for gethostbyaddr in -lbind... (cached) no

sudo aptitude install libggz-dev xlibs-dev libsdl-mixer1.2-dev

---

### Post by Tampio on 2007-03-04
libggz-dev is not in the repositories

---

### Post by Perfect Storm on 2007-03-04
Most be one of the special source I have in my repo. (you on dapper or edgy?)

Try without it and see how it work.

---

### Post by Tampio on 2007-03-04
I'm on dapper, and it still gives the same error messages as before.

---

### Post by Perfect Storm on 2007-03-04
Try compile a stable version of it and see if it's a success. It might be bugs in the development version.

---

### Post by Tampio on 2007-03-04
Make install in stable version gives these errors in the end 
> source='chatline.c' object='chatline.o' libtool=no \
        depfile='.deps/chatline.Po' tmpdepfile='.deps/chatline.TPo' \
        depmode=gcc3 /bin/sh ../../bootstrap/depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I../..  -I. -I./.. -I./../include -I../../utility -I../../common -I../../common/aicore -I../../intl -I./../agents -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -I/usr/include/freetype2 -g -O2 -DLOCALEDIR="\"/usr/local/share/locale\"" -DDEFAULT_DATA_PATH="\".:data:~/.freeciv:/usr/local/share/freeciv\""  -g -O2 -Wall -Wpointer-arith -Wcast-align -Wmissing-prototypes -Wmissing-declarations -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -c `test -f 'chatline.c' || echo './'`chatline.c
chatline.c: In function ‘inputline_return_callback’:
chatline.c:92: error: too few arguments to function ‘real_append_output_window’
chatline.c: In function ‘real_append_output_window’:
chatline.c:151: warning: passing argument 2 of ‘add_notify_window’ makes pointer from integer without a cast
chatline.c:151: error: too many arguments to function ‘add_notify_window’
make[2]: *** [chatline.o] Error 1
make[2]: Leaving directory `/home/janne/sorsat/freeciv-2.0.9/client/gui-sdl'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/janne/sorsat/freeciv-2.0.9/client'
make: *** [install-recursive] Error 1


---

### Post by Perfect Storm on 2007-03-04
Hmmm....sorry I can't help you here :-/

---

### Post by swodah on 2007-06-09
> **Tampio said:**
> Make install in stable version gives these errors in the end

I had the exactly same problem with Ubuntu Drapper and freeciv-2.0.9. However using sudo with both ./configure and make (sudo ./configure && make)  the problem went away...

Propably some lib has been installed with "wrong" permissions...

Hope that this helps...

---

