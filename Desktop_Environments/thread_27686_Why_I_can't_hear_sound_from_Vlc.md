---
title: "Why I can't hear sound from Vlc?"
date: 2005-04-17
forum: Desktop Environments
---

### Post by svizi on 2005-04-17
I am using Hoary. I am trying to play a xvid video file from vlc but i get no sound. The same video plays well at totem. Why is that happening?

---

### Post by coldturkey on 2005-04-17
I have the same problem with Xvid movies, it's probably AC3. Switch the default Audio codec to eSound (ESD) and it'll work fine :)

---

### Post by svizi on 2005-04-17
From where can I do that?

---

### Post by svizi on 2005-04-17
[QUOTE=svizi]From where can I do that?[/QUOTE]
 Probably I found it System->Preferences->Multimedia System Selector. Default Sink -> Output : ESD. Problem Solved.Thanks.

---

### Post by svizi on 2005-04-17
[QUOTE=svizi]Probably I found it System->Preferences->Multimedia System Selector. Default Sink -> Output : ESD. Problem Solved.Thanks.[/QUOTE]
 I have still the same problem with xmms!

---

### Post by coldturkey on 2005-04-17
Well, you just have to change XMMS to eSound too!
Rightclick > Alternativs > Setup (?) > Input for output (?) > Change to eSound libesdout.so
Sorry for the non-correct menu names, I'm using the swedish setup :)

---

### Post by svizi on 2005-04-18
[QUOTE=coldturkey]Well, you just have to change XMMS to eSound too!
Rightclick > Alternativs > Setup (?) > Input for output (?) > Change to eSound libesdout.so
Sorry for the non-correct menu names, I'm using the swedish setup :)[/QUOTE]
 Thanks.
For English Setup the menu names are Rightclick->Preferences->Audio I/O Plugins ->Output Plugin ->eSound.

Thnk you again...

---

