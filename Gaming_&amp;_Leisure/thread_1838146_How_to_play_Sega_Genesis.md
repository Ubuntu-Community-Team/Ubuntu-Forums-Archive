---
title: "How to play Sega Genesis"
date: 2011-09-03
forum: Gaming &amp; Leisure
---

### Post by honeybear on 2011-09-03
Hello,

Genesis is a console that was created by Sega. Sega creates games for computers and consoles. It is a well known company. 

If you have ever heard about this console and that you would know any information regarding this question, please do no hesitate to participate giving an hint.

After making some research using google, I could find a package for Ubuntu that was called "DGEN". After the download, I could install this application without too much problems by using the command:
```
sudo dpkg -i dgen_1.23-12_i386.deb
```

It reads files of bin extension. However it appears that none are working, although sometimes sega is displayed but does not remain long. 

I would be considering another alternative if possible. This would be a great opportunity for playing one old game that my old genesis was capable to offer me during many years. 

Thank you

---

### Post by blade4 on 2011-09-03
Why not try running a windows based emulator on wine ? I have a VGA emulator that actually runs better on wine than it does on my windows .

---

### Post by LowSky on 2011-09-03
Sega called the console the Mega Drive outside of the US, just a small reminder.

I'm using Arch and found these using yaourt, but a simple google search should help you

dgen-sdl
gden
generator
gens
gens-gs (seems to be the most popular on AUR.
kega-fusion
lxdream (sorry a Dreamcast emulator)
regen
yabause (Saturn Emulator)
yabause-qt (Saturn Emulator)

---

### Post by dodo3773 on 2011-09-03
Try "gens-gs". I have been using it for a while. It works pretty good.

Edit: LowSky beat me too it.__[URL="http://ubuntuforums.org/member.php?u=330216"]
[/URL]

---

### Post by honeybear on 2011-09-03
> **LowSky said:**
> Sega called the console the Mega Drive outside of the US, just a small reminder.

I'm using Arch and found these using yaourt, but a simple google search should help you

dgen-sdl
gden
generator
gens
gens-gs (seems to be the most popular on AUR.
kega-fusion
lxdream (sorry a Dreamcast emulator)
regen
yabause (Saturn Emulator)
yabause-qt (Saturn Emulator)


 Yabause for saturn 

```
apt-cache search generator sega
```
gives nothing :( 

[http://www.squish.net/generator/download.html](http://www.squish.net/generator/download.html) 
has no deb for ubuntu

---

### Post by honeybear on 2011-09-03
> **dodo3773 said:**
> Try "gens-gs". I have been using it for a while. It works pretty good.

Edit: LowSky beat me too it.__[URL="http://ubuntuforums.org/member.php?u=330216"]
[/URL]

I found it the gens-ds : 
[http://darkstar.ist.utl.pt/getdeb/ubuntu/pool/games/g/gens-gs/](http://darkstar.ist.utl.pt/getdeb/ubuntu/pool/games/g/gens-gs/)

is it supported by ubuntu ? since not official website

---

### Post by whatthefunk on 2011-09-03
```
@laptop:~$ apt-cache search sega
gxemul - machine emulator for multiple architectures
libgme-dev - Playback library for video game music files - development files
libgme0 - Playback library for video game music files - shared library
lilypond - A program for typesetting sheet music
rakarrack - Simple and easy guitar effects processor for GNU/Linux
rosegarden - music editor and MIDI/audio sequencer
yabause - beautiful and under-rated Saturn emulator
yabause-common - beautiful and under-rated Saturn emulator - common files
yabause-gtk - beautiful and under-rated Saturn emulator - Gtk port
yabause-qt - beautiful and under-rated Saturn emulator - Qt port
**dgen - Sega Genesis/MegaDrive emulator**
frogatto - 2D platformer game starring a quixotic frog
frogatto-data - 2D platformer game starring a quixotic frog
xjadeo - Video player with JACK sync
xmess-sdl - SDL binaries for the Multi Emulator Super System
xmess-x - X binaries for the Multi Emulator Super System
```

---

### Post by honeybear on 2011-09-03
> **whatthefunk said:**
> ```
@laptop:~$ apt-cache search sega
gxemul - machine emulator for multiple architectures
libgme-dev - Playback library for video game music files - development files
libgme0 - Playback library for video game music files - shared library
lilypond - A program for typesetting sheet music
rakarrack - Simple and easy guitar effects processor for GNU/Linux
rosegarden - music editor and MIDI/audio sequencer
yabause - beautiful and under-rated Saturn emulator
yabause-common - beautiful and under-rated Saturn emulator - common files
yabause-gtk - beautiful and under-rated Saturn emulator - Gtk port
yabause-qt - beautiful and under-rated Saturn emulator - Qt port
**dgen - Sega Genesis/MegaDrive emulator**
frogatto - 2D platformer game starring a quixotic frog
frogatto-data - 2D platformer game starring a quixotic frog
xjadeo - Video player with JACK sync
xmess-sdl - SDL binaries for the Multi Emulator Super System
xmess-x - X binaries for the Multi Emulator Super System
```

as I said in the thread, an alternative to dgen is looking forward, if it could be possible, easy to install..

---

### Post by dodo3773 on 2011-09-03
> **honeybear said:**
> I found it the gens-ds : 
[http://darkstar.ist.utl.pt/getdeb/ubuntu/pool/games/g/gens-gs/](http://darkstar.ist.utl.pt/getdeb/ubuntu/pool/games/g/gens-gs/)

is it supported by ubuntu ? since not official website

I think this is their website:

[http://segaretro.org/Gens/GS#Download](http://segaretro.org/Gens/GS#Download)

---

### Post by frenchn00b on 2011-09-03
> **dodo3773 said:**
> I think this is their website:

[http://segaretro.org/Gens/GS#Download](http://segaretro.org/Gens/GS#Download)


wow thank you very much. It is a very nice emulator. Very complete. so cool. 
[http://segaretro.org/images/7/75/Gens_2.16.7_i386.deb](http://segaretro.org/images/7/75/Gens_2.16.7_i386.deb)

---

### Post by bapoumba on 2011-09-03
Moved to Gaming.

---

### Post by whatthefunk on 2011-09-03
> **honeybear said:**
> as I said in the thread, an alternative to dgen is looking forward, if it could be possible, easy to install..

Yes, but you installed using a deb package.  Maybe the install was done incorrectly?  Try using the package in the repositories and install with apt-get.

---

