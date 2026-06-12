---
title: "Firefox 1.5 still not working"
date: 2005-12-31
forum: Desktop Environments
---

### Post by Timokl on 2005-12-31
I followed all the steps in [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) untill you should start Firefox 1.5 for the first time on the console with

```
firefox
```

This gives me two errors a number of times. First this one,

```
(firefox-bin:9860): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

```

then this one: 

```
(firefox-bin:9860): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden

```

I run Ubuntu Breezy 64Bit with this Kernel: 2.6.12-10-amd64-generic

What can I do to make Firefox running? I try to install Firefox since some days already, and I am quite frustrated already. :confused: 

Happy New Year 2006 to all of you!!!

---

### Post by thekiller on 2005-12-31
whats the output of [COLOR="Red"]locale[/COLOR]. Seems like en_US.UTF-8 isnt installed.
 Just do

```

sudo dpkg-reconfigure locales

```

---

### Post by Timokl on 2005-12-31
I tried that, but it did not change. The en_us.utf8 locale had been installed already. This is the output of the reconfiguration of the locales:

```
Generating locales...
  de_DE.UTF-8... done
  en_US.UTF-8... done
  de_AT.UTF-8... done
  de_BE.UTF-8... done
  de_CH.UTF-8... done
  de_LU.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
  th_TH.UTF-8... done
Generation complete.
```

I also checked about that missing pango files, firefox could not find (that's the meaning of the german error report) -- I can access it through the terminal without problems. :confused: 

The whole bunch of the pango errors is listed here:

```
(firefox-bin:19080): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:19080): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:19080): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:19080): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:19080): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:19080): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:19080): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:19080): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:19080): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:19080): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:19080): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:19080): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:19080): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: Kann die Shared-Object-Datei nicht öffnen: Datei oder Verzeichnis nicht gefunden
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:19080): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
```

What could be the problem? Anybody with an idea???

---

### Post by Timokl on 2005-12-31
Nearly forgot: When I type **locale** into the terminal, this is what I get:

```
LANG=de_DE.UTF-8
LC_CTYPE="de_DE.UTF-8"
LC_NUMERIC="de_DE.UTF-8"
LC_TIME="de_DE.UTF-8"
LC_COLLATE="de_DE.UTF-8"
LC_MONETARY="de_DE.UTF-8"
LC_MESSAGES="de_DE.UTF-8"
LC_PAPER="de_DE.UTF-8"
LC_NAME="de_DE.UTF-8"
LC_ADDRESS="de_DE.UTF-8"
LC_TELEPHONE="de_DE.UTF-8"
LC_MEASUREMENT="de_DE.UTF-8"
LC_IDENTIFICATION="de_DE.UTF-8"
LC_ALL=

```

However, the en_US.utf8 locale is installed and available, see **locale -a**

```
C
de_AT.utf8
de_BE.utf8
de_CH.utf8
de_DE.utf8
de_LU.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_IN.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX
th_TH.utf8
```

And ...

[CENTER][SIZE="6"][COLOR="Red"]Happy New Year 2549 to everybody!!![/COLOR][/SIZE]
... at least according to the buddhist calender which is in use in thailand :smile: [/CENTER]

---

