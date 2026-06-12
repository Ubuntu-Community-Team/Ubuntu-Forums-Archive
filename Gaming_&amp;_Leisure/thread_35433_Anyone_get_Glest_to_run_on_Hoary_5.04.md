---
title: "Anyone get Glest to run on Hoary 5.04?"
date: 2005-05-18
forum: Gaming &amp; Leisure
---

### Post by Z-Bo on 2005-05-18
I installed glest 1.0.10-7 and glest-data 1.0.10 from the debian repository: 

[http://www.linex.org/sources/linex/debian/](http://www.linex.org/sources/linex/debian/) cl juegalinex 

When running glest from the terminal my screen blinked really quick and then this error output appeared:

```
john@seed:~ $ glest
ln: `/home/john/.glest/bin': File exists
ln: `/home/john/.glest/lib': File exists
void Shared::Platform::Window::setStyle(Shared::Platform::WindowStyle) not implemented.
void Shared::Platform::Window::setBounds(int, int, int, int) not implemented.
virtual void Shared::Platform::PlatformContextGl::makeCurrent() not implemented.OpenAL Vendor: J. Valenzuela
OpenAL Version: 0.0.7
OpenAL Renderer: Software
OpenAl Extensions: Software
open /dev/[sound/]dsp: Device or resource busy
Exception: Couldn't open audio device.
Warning: glIsList failed for font.
Warning: glIsList failed for font.
Warning: glIsList failed for font.
Warning: glIsList failed for font.
Warning: glIsList failed for font.
Warning: glIsList failed for font.
```

I have very little insight into what these warnings and error messages mean.  I tried searching the web (using google) and the only site which mentions "Warning: glIsList failed for font" is written in a foreign language I have not yet learned.  I then searched the Ubuntu Forums for information and nothing returned.  HappyPenguin.org forums mention that Glest has some audio problems on Linux, but  there was no how-to guide in how to overcome it.

Is this a dead end?

---

### Post by jdodson on 2005-05-19
try doing a forum search for esd.  killing that proccess might allow you to run the game, it has for others.

to answer your question, i have it running on my machine here.  i used the download linux file, not a deb though.

[QUOTE=Z-Bo]I installed glest 1.0.10-7 and glest-data 1.0.10 from the debian repository: 

[http://www.linex.org/sources/linex/debian/](http://www.linex.org/sources/linex/debian/) cl juegalinex 

When running glest from the terminal my screen blinked really quick and then this error output appeared:

```
john@seed:~ $ glest
ln: `/home/john/.glest/bin': File exists
ln: `/home/john/.glest/lib': File exists
void Shared::Platform::Window::setStyle(Shared::Platform::WindowStyle) not implemented.
void Shared::Platform::Window::setBounds(int, int, int, int) not implemented.
virtual void Shared::Platform::PlatformContextGl::makeCurrent() not implemented.OpenAL Vendor: J. Valenzuela
OpenAL Version: 0.0.7
OpenAL Renderer: Software
OpenAl Extensions: Software
open /dev/[sound/]dsp: Device or resource busy
Exception: Couldn't open audio device.
Warning: glIsList failed for font.
Warning: glIsList failed for font.
Warning: glIsList failed for font.
Warning: glIsList failed for font.
Warning: glIsList failed for font.
Warning: glIsList failed for font.
```

I have very little insight into what these warnings and error messages mean.  I tried searching the web (using google) an


d the only site which mentions "Warning: glIsList failed for font" is written in a foreign language I have not yet learned.  I then searched the Ubuntu Forums for information and nothing returned.  HappyPenguin.org forums mention that Glest has some audio problems on Linux, but  there was no how-to guide in how to overcome it.

Is this a dead end?[/QUOTE]

---

### Post by J.K.Makowka on 2005-05-20
I installed glest with the loki installer from [www.liflg.org](www.liflg.org)
Works great, without changing anything.

---

### Post by Burgundavia on 2005-05-21
I have gotten the .debs working in Hoary. Also, they are being reviewed right now to see if they pass muster. If they do, they should be in Breezy. No timetable on that, however.

Corey

---

### Post by skoal on 2005-05-21
I'm using glest 1.0.10-7 and glest-data 1.0.10 debian packages and they work fine for me on hoary.

kernel  2.6.11-1-686
nvidia 7174

* all debian packages from repos (and nothing custom).

---

### Post by hindiogine on 2005-07-15
Glest on Ubuntu 5.04

I installed the debs and the game loads fine.  I can configure but when it starts I can only hear the music and see all _grey_     There is a sort of map at the top left corner with some red rectangles.   I can hear the music.

That is all.

What can I do to play this promising game?

Thanks in advance

cisei

---

### Post by jdodson on 2005-07-15
[QUOTE=hindiogine]Glest on Ubuntu 5.04

I installed the debs and the game loads fine.  I can configure but when it starts I can only hear the music and see all _grey_     There is a sort of map at the top left corner with some red rectangles.   I can hear the music.

That is all.

What can I do to play this promising game?

Thanks in advance

cisei[/QUOTE]

did you configure you 3D video to work?  if not, poke around the forums, there are ample threads to help you out in this area.

---

### Post by ]tux[cHriz on 2005-07-16
I used the installer from liflg.org. Works fine! 

greetz from German Ubuntu Community ;)
chris

---

### Post by RastaMahata on 2005-07-17
the installers from liflg.org work great on ubuntu. Just download the file, make it executable (right click, properties, third tab, and give exec permissions to the owner), then exit the properties window, and double click on the file... easy!

---

### Post by hindiogine on 2005-07-17
[QUOTE=jdodson]did you configure you 3D video to work?  if not, poke around the forums, there are ample threads to help you out in this area.[/QUOTE]
 jdodson,

yes my nvidia drivers work.  I get the Nvidia logo at bootup.

I am downloading now the liflg.org glest_1.1.0 file using bittorrent.

cisei

---

### Post by hindiogine on 2005-07-17
[QUOTE=']tux[cHriz']I used the installer from liflg.org. Works fine! 

greetz from German Ubuntu Community ;)
chris[/QUOTE]
 Chris,

Am I supposed to download also the Loki installer before I do the glest download?  Or are they separate things?

I am downloading now glest_1.1.0-multilanguage.run.  Is that all I need?

Thanks!

cisei

---

