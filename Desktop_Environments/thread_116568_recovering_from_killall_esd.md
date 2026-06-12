---
title: "recovering from killall esd"
date: 2006-01-13
forum: Desktop Environments
---

### Post by blacklantern on 2006-01-13
I currently have to do a 'killall esd' in order to hear the sound in Neverwinter Nights, and there is naturally no sound when I exit the game. I'm looking for a way to get the sound working short of a reboot. I saw this thread:

[http://ubuntuforums.org/showthread.php?t=56267&highlight=killall+esd]("http://ubuntuforums.org/showthread.php?t=56267&highlight=killall+esd")

But the solution there isn't helping me. Any suggestions would be highly appreciated.

---

### Post by cwaldbieser on 2006-01-13
[QUOTE=blacklantern]I currently have to do a 'killall esd' in order to hear the sound in Neverwinter Nights, and there is naturally no sound when I exit the game. I'm looking for a way to get the sound working short of a reboot. I saw this thread:

[http://ubuntuforums.org/showthread.php?t=56267&highlight=killall+esd]("http://ubuntuforums.org/showthread.php?t=56267&highlight=killall+esd")

But the solution there isn't helping me. Any suggestions would be highly appreciated.[/QUOTE]
Do you have multiple soundcards or some other strange config?  Because the "esd" command should start esd running again.  Try running it in the foreground (without the "&") and see if there is an error.

---

### Post by Thirsteh on 2006-01-13
A background daemon (&) would still output error messages in the window it was launched from :)

---

### Post by blacklantern on 2006-01-13
[QUOTE=cwaldbieser]Do you have multiple soundcards or some other strange config?  Because the "esd" command should start esd running again.  Try running it in the foreground (without the "&") and see if there is an error.[/QUOTE]

Interesting... I always knew that the esd daemon was running again, but for some reason I couldn't hear sound from gaim anymore. However, the sound from totem video player works. I should have been more specific. Both applications produced sound before, but only Gaim is no longer producing sound.

---

