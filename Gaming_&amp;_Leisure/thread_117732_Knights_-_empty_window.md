---
title: "Knights - empty window"
date: 2006-01-15
forum: Gaming &amp; Leisure
---

### Post by lrmall01 on 2006-01-15
I just installed the chess program.  Seemed to go fine, apt-get didn't have any complaints.  When I start the program up I just get an empty window.  All the menus are there and they work.  I can start new games, connect to FICS, etc. but there is no board.  Just the window and the menu bar.

When I start the program in a terminal, here is the output:

lrmall01@crom:~$ knights
knights: WARNING: audio::audio: Can not create Arts::SoundServerV2
knights: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'tar'.
knights:
knights: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'tar'.
knights:
knights: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'tar'.
knights:
knights: WARNING: The theme KBDefault.tar.gz does not exist in any valid path.
knights: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'tar'.
knights:
knights: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'tar'.
knights:
knights: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'tar'.
knights:
knights: WARNING: The theme KCDefault.tar.gz does not exist in any valid path.
knights: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'tar'.
knights:
knights: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'tar'.
knights:
knights: ERROR: : couldn't create slave : Unable to create io-slave:
klauncher said: Unknown protocol 'tar'.
knights:
knights: WARNING: The theme KSDefault.tar.gz does not exist in any valid path.
QFile::open: No file name specified
QFile::open: No file name specified
QFile::open: No file name specified
QFile::open: No file name specified
QFile::open: No file name specified
QFile::open: No file name specified
QFile::open: No file name specified
QFile::open: No file name specified
QMetaObject::findSignal:io_engine: Conflict with io_base::sendCMD(const Command&)

Any suggestions?  BTW, I'm runnung ubuntu, breezy.  Thought it might be something to do with not having all the KDE libs installed, but I don't think so - all the menus work correctly.

Thanks.

Edit:  Seems that it can't find the themes.  I checked the installed files and it shows the default theme file got installed to /usr/share/apps/knights/themes/KSDefault.tar.gz  I tried the suggestions located here, [http://knights.sourceforge.net/faq.php](http://knights.sourceforge.net/faq.php), like the -d command line switch but haven't got it to work yet.

The terminal states that the theme KSDefault.tar.gz does not exist in any valid path.  So, what is a valid path - I can find the archive for the themes, but I can't figure out how to get the app to find them.

---

### Post by Mr_Grieves on 2006-01-15
I think this is the biggest clue to you're problem.

> 
klauncher said: Unknown protocol 'tar'.

It seems your system tries to open/use a file with a .tar prefix.. but it does not recognice it.

Weird.. could it be the path to 'tar' that is broken?

What does:
```

whereis tar

```
give?

---

### Post by lrmall01 on 2006-01-15
lrmall01@crom:~$ whereis tar
tar: /bin/tar /usr/include/tar.h /usr/share/man/man1/tar.1.gz

---

### Post by lrmall01 on 2006-01-19
Shameless bump... I still haven't got this figured out.

---

### Post by 146lily on 2006-01-20
I have the same problem, both board and pieces are missing. I downloaded a theme pack from the knights website. Put it in home and used knights options to install themes. I got a choice of boards with their own pieces, I want to choose seperatly...
If you look round in I think user folder you will also find basic default theme to load.
Dont know why it wont install itself!

---

### Post by lrmall01 on 2006-01-21
I'm not quite sure we have the same problem.  I downloaded themes as well and installed locally with no change.  In the settings dialog it shows that it should use the default themes but nothing works.

---

### Post by kalias on 2006-02-05
Interesting what you have seen because it is exactly what I see on my system.  I thought it was due to my upgrade but apparently not.  Is there a system type person out there that can try it on there system and see if it works?  

kalias

---

### Post by BlueEars on 2006-02-07
Hi

Did you ever solve this empty window problem?

I like to play chess at Icc. And I want to give this program a try. But I also suffer from the empty window problem.


Help!

:confused:

---

### Post by lrmall01 on 2006-02-09
No, never did get it figured out.  eBoard is a nice client though, have you tried it?  I also found Jose [http://jose-chess.sourceforge.net/](http://jose-chess.sourceforge.net/)
, but I'm not sure it can play on chess servers such as ICC.  It is really nice for analyzing positions are practicing tactics from FEN positions or pgn databases.

---

### Post by sp3ci3s on 2006-03-26
just install the package kdebase-kio-plugins and everything works fine, at least for me.

---

### Post by lrmall01 on 2006-03-26
Yep, works for me too!  Thanks.

---

### Post by edwina on 2006-06-02
Sorry for resurrecting an old thread, but it looks like this problem recurs in Dapper and doesn't get solved by the kdebase-plugins fix. Have you guys upgraded yet? Still working okay?

---

### Post by faetux on 2006-09-09
@edwina

I solvead the dapper-problem for me. I start knights with --noxim

---

### Post by UbuGianlu on 2008-03-29
confirm miss kio plugins

if you have automatic update active after you install knights you get message update available, run the update everythings works fine.

:popcorn:

---

