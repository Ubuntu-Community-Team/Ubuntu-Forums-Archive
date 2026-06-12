---
title: "issue with flash on 9.10"
date: 2010-02-27
forum: Desktop Environments
---

### Post by gixpaulie on 2010-02-27
Hi all,

Just come across something today and its doing my head in. It all started when it asked to install the flash plugin when i accessed a youtube vid and once i install the plugin a tried watching the vid and when i click the play/scanbar/or try to adjust the volume they dont work properly but if i randomly click them then the button sometime works for that one moment only. Its really weird if i go to google vid does the same thing and even install the beta of google chome and thats the same, but if i go to adobe flash page where theres a animation showing you flash is installed that runs fine and the play/pause and volume works prefectly


as anyone come across this before , or has any sugguestions what it could be

ps its 64bit aswell

many thanks

---

### Post by talhaguy on 2010-02-27
Yeah that's strange. This happens to me when I use Opera. The YouTube buttons don't respond properly, if they respond at all. Firefox and Chrome treat me well though. Hopefully with HTML 5 we won't need to depend on flash as much.

---

### Post by Kakers on 2010-02-27
Yea I had a lot of problems with this and found out it was to do with a compatability problem between flash + compiz. when I disabled compiz the buttons started working again.

Apparently it only happens on 64bit.

Fix:
System -> Prefrences -> Apperance
On the Visual Effects tab select 'None'

Finally got it working now with compiz and that was simply trying to install it a whole load of different ways:

[http://www.google.co.uk/search?q=flash+on+64+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a](http://www.google.co.uk/search?q=flash+on+64+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a)

Think I used nonfree-flashplugin...

---

### Post by Foxcow on 2010-02-27
> **gixpaulie said:**
> Hi all,

Just come across something today and its doing my head in. It all started when it asked to install the flash plugin when i accessed a youtube vid and once i install the plugin a tried watching the vid and when i click the play/scanbar/or try to adjust the volume they dont work properly but if i randomly click them then the button sometime works for that one moment only. Its really weird if i go to google vid does the same thing and even install the beta of google chome and thats the same, but if i go to adobe flash page where theres a animation showing you flash is installed that runs fine and the play/pause and volume works prefectly


as anyone come across this before , or has any sugguestions what it could be

ps its 64bit aswell

many thanks


I had the exact same problem but its fixed now and works beautifully.

Post #5 is your solution:
[http://ubuntuforums.org/showthread.php?t=1391532](http://ubuntuforums.org/showthread.php?t=1391532)

---

### Post by wyleb2 on 2010-03-01
> **Kakers said:**
> Yea I had a lot of problems with this and found out it was to do with a compatability problem between flash + compiz. when I disabled compiz the buttons started working again.

Apparently it only happens on 64bit.

Fix:
System -> Prefrences -> Apperance
On the Visual Effects tab select 'None'



Wow that was easy.  Thanks, I tried 2 other fixes that ppl swore by but did nothing, and a lot of re-installations, but this finally did the trick.

---

