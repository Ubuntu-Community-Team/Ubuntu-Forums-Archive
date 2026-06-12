---
title: "FireFox broken?"
date: 2005-12-23
forum: General Help
---

### Post by DJiNN on 2005-12-23
Is FireFox somewhat broken or having problems (Release 1.5)? The reason that i ask is, almost everytime i fire it up now & try & do certain things, it crashes..... almost every time. So much so that i have now had to resort to using Epiphany (Which is OK, i quite like it) & Opera..... Not that i mind, but i have seen a few people complain about problems with this version of FireFox...... just wondered if anyone else has had any problems?

DJiNN

---

### Post by DarkAngel88 on 2005-12-23
I allready had this problem once, and solve it by starting with a brand new profile.

To do so, I completly removed the .mozilla directory.  I had to restore all my themes, extensions and bookmarks but that was the only thing that actualy work with the multiple crashes of firefox.

Here is the command...

```
sudo rm -R ~/.mozilla
```

Like I said.. might be drastic but it work for me !

---

### Post by kaamos on 2005-12-23
My installation of ff 1.5 segfaults maybe once or twice in two weeks. Not much, but still annoying when it happens.. It usually (but not always!) occurs when a plugin is loaded.

---

### Post by angkor on 2005-12-23
I'm running 1.5 for about a 5 days now and it hasn't crashed on me so far...knock...knock. Can you tell us where (on what site) it crashes or does it happen at random?

---

### Post by Elrohir on 2005-12-23
What I've learned from the Firefox newsgroup is that if Firefox crashes, the first thing to see is that an extension is doing this...

```
$ ~/firefox/firefox -safe-mode (this disables themes and extensions)
``` if the crashing stops, then its a buggy theme or extension... then you have to create a new profile...

```
$ ~/firefox/firefox -p (opens profile manager)
``` press New Profile and create a new profile and then run Firefox...

to import the bookmarks, go to ~/.mozilla/firefox and there you'll find bookmarks.html and bookmarks.bak, copy those two and paste them in the new profile... for extensions and themes... well... reinstall them... one by one...

---

### Post by punkr0x on 2005-12-23
I had lots of problems with 1.5, switched back to 1.07 for the time being.

---

