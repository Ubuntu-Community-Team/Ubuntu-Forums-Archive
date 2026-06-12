---
title: "how to enable mp4/aac/m4a Support in easyTag?"
date: 2006-03-25
forum: Desktop Environments
---

### Post by Bazon on 2006-03-25
Hello!

In [EasyTAG](http://easytag.sourceforge.net/) 1.99.10 from the Ubuntu 5.10 Repositories, the support for mp4/aac/m4a files is disabled: See it in the menu *help > about*.

But I'd like to tag m4a files!

so how do I enable it?

Do I have to build it from source? 
I'd like to avoid that, as that leads to a chain of other source installations ([id3lib](http://easytag.sourceforge.net/downloads.htm#id3lib), [MPEG4IP](http://mpeg4ip.sourceforge.net/) ...) and I don't know where the dependency chain will end...

So if there is another way (Ubuntu package?), that would be great!
Does anyone know something?

Thanks,
Bazon

---

### Post by o_fortuna on 2006-03-25
[QUOTE=Bazon]Hello!

In [EasyTAG](http://easytag.sourceforge.net/) 1.99.10 from the Ubuntu 5.10 Repositories, the support for mp4/aac/m4a files is disabled: See it in the menu *help > about*.

But I'd like to tag m4a files!

so how do I enable it?

Do I have to build it from source? 
I'd like to avoid that, as that leads to a chain of other source installations ([id3lib](http://easytag.sourceforge.net/downloads.htm#id3lib), [MPEG4IP](http://mpeg4ip.sourceforge.net/) ...) and I don't know where the dependency chain will end...

So if there is another way (Ubuntu package?), that would be great!
Does anyone know something?

Thanks,
Bazon[/QUOTE]
You can get a package (not from the Ubuntu repositories) here: [http://http.us.debian.org/debian/pool/main/e/easytag/easytag_1.99.11-1_i386.deb]("http://http.us.debian.org/debian/pool/main/e/easytag/easytag_1.99.11-1_i386.deb")

Frankly, I don't know if this will work any better. But, it's worth a shot. To install it, download the file, save it to your desktop, then open up a terminal (Applications-->Accessories-->Terminal) and paste in these commands:
```
cd Desktop
sudo apt-get remove easytag
sudo dpkg -i easytag_1.99.11-1_i386.deb
```

---

### Post by Bazon on 2006-03-26
Thanks, but again strange dependencies:

[i]"Abhängigkeitsprobleme" = dependency problems
"hängt ab von " = depends on
"bereitstellt, ist nicht installiert" = available, but not installed
"Fehler traten auf beim Bearbeiten von" = prpblems while making[/i]
> $ sudo dpkg -i easytag_1.99.11-1_i386.deb
Wähle vormals abgewähltes Paket easytag.
(Lese Datenbank ... 95320 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke easytag (aus easytag_1.99.11-1_i386.deb) ...
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von easytag:
 easytag hängt ab von libcairo2 (>= 1.0.2-2); aber:
  Version von libcairo2 auf dem System ist 1.0.2-0ubuntu1.1.
 easytag hängt ab von libgcc1 (>= 1:4.0.2); aber:
  Version von libgcc1 auf dem System ist 1:4.0.1-4ubuntu9.
 easytag hängt ab von libid3-3.8.3c2a; aber:
  Paket libid3-3.8.3c2a bereitstellt, ist nicht installiert.
 easytag hängt ab von libstdc++6 (>= 4.0.2-4); aber:
  Version von libstdc++6 auf dem System ist 4.0.1-4ubuntu9.
 easytag hängt ab von libxrender1 (>> 1:0.9.0-1); aber:
  Version von libxrender1 auf dem System ist 1:0.9.0-1.
dpkg: Fehler beim Bearbeiten von easytag (--install):
 Abhängigkeitsprobleme - lasse es unkonfiguriert
Fehler traten auf beim Bearbeiten von:
 easytag
So again a bunch of packages needed I don't know where to get from - it seems as if it doesn't "like" the Ubuntu versions...

---

### Post by Bazon on 2006-03-26
OK, I tried to build easytag from source now.
With *./configure *was everything all right, but *make* made some problems:

[i]"Fehler" = error
"Zeiger" = pointer
"verlasse Verzeichnis" = leave directory[/i]
rest should be clear i think...

> $ make
...
In file included from /usr/include/mpeg4ip.h:28,
                 from /usr/include/mp4.h:27,
                 from mp4_header.c:44:
/usr/include/systems.h:248: Fehler: syntax error before »__extension__«
/usr/include/systems.h:248: Fehler: syntax error before »&&« token
mp4_header.c:61: Fehler: »MP4_MPEG4_AAC_HE_AUDIO_TYPE« ist hier nicht deklariert (nicht in einer Funktion)
mp4_header.c: In Funktion »getType«:
mp4_header.c:125: Warnung: implizite Deklaration der Funktion »MP4GetTrackMediaDataName«
mp4_header.c:125: Warnung: Initialisierung erzeugt Zeiger von Ganzzahl ohne Typkonvertierung
mp4_header.c: In Funktion »Mp4_Header_Read_File_Info«:
mp4_header.c:240: Warnung: implizite Deklaration der Funktion »MP4GetTrackAudioChannels«
make[3]: *** [mp4_header.o] Fehler 1
make[3]: Verlasse Verzeichnis »/home/me/easytag/easytag-1.99.11/src«
make[2]: *** [all-recursive] Fehler 1
make[2]: Verlasse Verzeichnis »/home/me/easytag/easytag-1.99.11/src«
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis »/home/me/easytag/easytag-1.99.11«
make: *** [all] Fehler 2
any ideas?

---

### Post by Hebus95 on 2006-10-01
.

---

### Post by Hebus95 on 2006-10-01
It should be quite interresting :
[http://www.ubuntuforums.org/archive/index.php/t-103374.html](http://www.ubuntuforums.org/archive/index.php/t-103374.html)

---

