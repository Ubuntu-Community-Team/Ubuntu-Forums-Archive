---
title: "Weird wine crash"
date: 2007-04-12
forum: Gaming &amp; Leisure
---

### Post by Tellisk on 2007-04-12
Okay, so earlier today I was playing World of Warcraft just fine. I turn off my computer (there was an update that had been bugging me to reboot since like 2 days ago), go to class. I come back about 2-3 hours later and turn it on. Now when I try doing anything in Wine (WoW, Ventrilo, winecfg), I get sent back to the Ububtu log-in screen.

I apologize for posting this in two forums, but my other post was initially about a different issue.
I hope someone can help because I'm stumped.

Oh yeah, I've tried reinstalling Wine and Rebooting. Neither worked. And I'm running Ubuntu 6.10 with the latest version of wine.

---

### Post by Tellisk on 2007-04-12
I want to try removing Wine and starting over with a fresh install, but will this affect the files I have installed via Wine already? Installing WoW and tBC is such a long tedious process that I'd like to know I'm getting myself into it before I go getting myself into it =)

---

### Post by willskills on 2007-04-12
No, WoW is a client, you don't need to install it, just move the World of Warcraft directory elsewhere :)

---

### Post by Tellisk on 2007-04-12
Ok thanks. I'll try that. Erm... what command can I type to remove wine?

---

### Post by willskills on 2007-04-12
sudo apt-get remove wine  - I think, although fairly new to ubuntu myself.

---

### Post by Tellisk on 2007-04-12
Well, I'm officially frustrated. I removed it and reinstalled it and tried running winecfg, and got booted to the log-in screen again.

---

### Post by willskills on 2007-04-12
Beyond my knowledge to fix mate, maybe someone else will know something more :)

---

### Post by Tellisk on 2007-04-12
Yeah, thanks for trying though =)

---

### Post by david_kt on 2007-04-13
Try to rename your wine folder ~/.wine to other name (~/.wine_old for example), and then try again winecfg and let me know what happened.

DK

---

