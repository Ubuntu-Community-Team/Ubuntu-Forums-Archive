---
title: "Organize Music"
date: 2005-09-04
forum: Desktop Environments
---

### Post by binarymelon on 2005-09-04
I'm wondering if there are any applications, using gtk that can connect to musicbrainz for use in tagging music.  Also does anyone know of a quick way I can organize my music based on the id3 tags.  I've tried running MusicBrainz through wine, and also using VMWare and a Samba share, but in wine it doesn't work well and running VMWare uses up far too many resources, for my little machine.

 [-X Remember, I said gtk  :-P

---

### Post by banjobacon on 2005-09-04
[QUOTE=binarymelon]I'm wondering if there are any applications, using gtk that can connect to musicbrainz for use in tagging music.  Also does anyone know of a quick way I can organize my music based on the id3 tags.  I've tried running MusicBrainz through wine, and also using VMWare and a Samba share, but in wine it doesn't work well and running VMWare uses up far too many resources, for my little machine.

 [-X Remember, I said gtk  :-P[/QUOTE]
 EasyTag can organize your files into directories based on tags. It took me a while to figure out the program's interface, but after after figuring it out, it was rather easy.

I don't know about MusicBrainz, though.

---

### Post by binarymelon on 2005-09-04
I've been looking at another program that I had tried a couple of months ago.  It's called Picard, but as before I am unable to get it to run, and I get the following output.  If anyone suggest a fix for this it would be appreciated.

```
Gtk-WARNING **: Unable to locate loadable module in module_path: "libbluecurve.so",
Traceback (most recent call last):
  File "./tagger.py", line 58, in ?
    from browser import browser, filelookup, launch
  File "/home/ryan/Desktop/picard-0.5.0-test2/browser/browser.py", line 57, in ?    from lib import events, util
  File "/home/ryan/Desktop/picard-0.5.0-test2/lib/util.py", line 73, in ?
    class ConfigSettings(object):
  File "/home/ryan/Desktop/picard-0.5.0-test2/lib/util.py", line 95, in ConfigSettings
    settingID3Encoding = tunepimp.eUTF8
AttributeError: 'module' object has no attribute 'eUTF8'
```

---

### Post by binarymelon on 2005-09-05
bump

---

### Post by rdwtux on 2005-09-05
Did you install the software via redhat RPM's?

Bluecurve is redhat/fedora's default theme for gnome/kde.

---

### Post by greyhound4334 on 2005-09-05
I use the muscibrainz client under Crossover Office, which is a commercialized verison of wine.  Crossover makes wine far easier to install and administer (at least it did as of a year ago when I tried wine).  Musicbrainz works fine in this environment.  As does Microsoft Office, Photoshop, Dreamweaver MX and IE6, among other things.

---

### Post by rum beverage on 2005-09-07
I should have said crossover office when I posted earlier.  When I said wine that is what I was referring to.  It does not run well.  It usually stops responding.

[QUOTE=rdwtux]Did you install the software via redhat RPM's?

Bluecurve is redhat/fedora's default theme for gnome/kde.[/QUOTE]

That's just a warning and wouldn't cause the program to not run.  At least I'm fairly certain it wouldn't.  And I'm just running it from source downloaded from the musicbrainz site.

---

### Post by gorkhal on 2005-09-07
[QUOTE=binarymelon]I'm wondering if there are any applications, using gtk that can connect to musicbrainz for use in tagging music.  Also does anyone know of a quick way I can organize my music based on the id3 tags.  I've tried running MusicBrainz through wine, and also using VMWare and a Samba share, but in wine it doesn't work well and running VMWare uses up far too many resources, for my little machine.

 [-X Remember, I said gtk  :-P[/QUOTE]

You can try Ex Falso for ID3 tagging. Great software get it [HERE](http://www.sacredchao.net/quodlibet/wiki) or follow the excellent howto for 'Quod Libet' in the Tips and Tricks section.

---

