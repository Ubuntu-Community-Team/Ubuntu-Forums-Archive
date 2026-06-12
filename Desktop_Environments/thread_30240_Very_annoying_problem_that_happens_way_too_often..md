---
title: "Very annoying problem that happens way too often."
date: 2005-04-27
forum: Desktop Environments
---

### Post by Ricapar on 2005-04-27
At random, when I open any program, the little sound that is played it is opened gets looped over and over, not stopping. Everything else starts locking up, menus refuse to open, things won't close. I can't even get it to reboot properly after it does that.

Has anyone had a problem like this, or have any idea what is causing it?

---

### Post by verzonen on 2005-04-27
I have not seen that problem, but then again I have turned of all system sounds as it interfeers with my internet radio, maybe turning of al system sounds is an option for you??

---

### Post by Ricapar on 2005-04-27
I'll give it a try.

I'll leave it like that for about a day, I'll repost what happens afterwards.

---

### Post by tread on 2005-04-27
If it repeats, you might want to file in a bug report.

---

### Post by Ricapar on 2005-04-29
I've been messing with it for a while, and it's not just system sounds, it's _any_ sound.

It seems to happen when I leave the computer alone for a while. If I come back and use anything that will make a sound, the first part of that sound will keep looping forever, and lock up the system.

I believe it's a problem with esound/polypaudio. When I had esound installed, it would loop the sound on forever while locking up the system. I started messing around, and installed polypaudio, replacing esound. The problem with the sound looping was still there, but this time it didn't lock up the system. The forever loop is still triggered when the computer is left alone, and then set to make a sound.

This is starting to drive me nuts, I like going for a long snack every once in a while, and when I get back I usually end up having to restart my computer or unplug my speakers because of it :(

---

