---
title: "Scandinavian characters don't work in IRC after installing a fresh hoary"
date: 2005-04-08
forum: Desktop Environments
---

### Post by Joonas on 2005-04-08
Thought for some reason to clean my system up a bit and installed the official Hoary from CD over my previously from Warty dist-upgraded Hoary. The install succeeded well but now in IRC my ä and ö don't show properly for other users and their ones don't show right in my clients, Irssi and XChat. 

I don't think it isn't the keyboard layout because I currently have Finnish layout selected (it worked before in Warty even after upgrading). I also myself see my characters correctly. What other causes could there be?

---

### Post by olpe on 2005-09-09
Well I am having the same problem, but quick fix for that is to start irssi with command: LC_CTYPE=fi_FI irssi

---

### Post by blueturtl on 2005-09-09
The problem also seems to extend over to Evolution.

My guess is this has something to do with localization. I'm using an english language version of Hoary with a Finnish keyboard, and if I remember correctly, Finland as my locality. Can this be changed afterwards to let's say England or USA without meddling with the timezones etc?

---

### Post by blueturtl on 2005-09-12
> Thought for some reason to clean my system up a bit and installed the official Hoary from CD over my previously from Warty dist-upgraded Hoary. The install succeeded well but now in IRC my ä and ö don't show properly for other users and their ones don't show right in my clients, Irssi and XChat.

See what you can make of this: [http://ubuntuforums.org/showthread.php?t=64761](http://ubuntuforums.org/showthread.php?t=64761)

---

