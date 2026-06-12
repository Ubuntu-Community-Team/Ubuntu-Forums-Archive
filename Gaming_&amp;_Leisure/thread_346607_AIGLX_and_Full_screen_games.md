---
title: "AIGLX and Full screen games"
date: 2007-01-25
forum: Gaming &amp; Leisure
---

### Post by cwood06 on 2007-01-25
I was wondering if there was a way to make games run in ful lscreen with aiglx/beryl.

I found a work around which was 

1. Load up WoW w/ metacity
2. Once wow is loaded up swich over to beryl and it will still load the game in full screen.

I tryed to make a seprate x server to load the game into but that didnt work. Does anyone know a way to make it so the game loads up to default with out me doing this small work around?

---

### Post by Sammi on 2007-01-26
Games aren't very stable under Beryl/Compiz+AIGLX and usually don't run at all or even result in your computer crashing if you try to run it in Xgl.

If you are using AIGLX then it should be sufficient to turn Beryl or Compix off, which should be easy enough to do. Don't know very much about where and how you change settings in Compiz, because  I use Beryl. But in Beryl you can change between metacity and beryl in the system tray icon it has. It may work the sane way in Compiz

---

### Post by Eazy© on 2007-01-26
This is a script I use to play UT2004.
```
#!/bin/bash

killall -s USR2 beryl-manager
ut2004 $@ ;
killall -s USR2 beryl-manager
beryl & emerald --replace &
exit 0
```

Perhaps you can edit this script with remove ut2004 in the script and add the command you use to start your game.

I have posted this script [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?p=2063433#post2063433")

---

