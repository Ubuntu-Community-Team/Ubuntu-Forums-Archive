---
title: "MS Core Fonts on Ubuntu"
date: 2005-03-15
forum: Desktop Environments
---

### Post by casualtie on 2005-03-15
Since I got a Window XP cd I got the right to use MS Core Fonts.
So, I want to install them on my Ubuntu system.
But I do not know how. 

I have tried pasted them into /usr/share/fonts, but that did not work :P

Do anyone know how to install these fonts?
I run Gnome and Warty Warthog.

-Thanks

---

### Post by bored2k on 2005-03-15
[QUOTE=casualtie]Since I got a Window XP cd I got the right to use MS Core Fonts.
So, I want to install them on my Ubuntu system.
But I do not know how. 

I have tried pasted them into /usr/share/fonts, but that did not work :P

Do anyone know how to install these fonts?
I run Gnome and Warty Warthog.

-Thanks[/QUOTE]
 sudo apt-get install msttcorefonts [in a terminal window]
if it can not find the file, open synaptic package manager > settings > repositories and checkmark [on] universe/multiverse and retry.

---

### Post by casualtie on 2005-03-15
Ah, so their actually public? :)
Thanks, that worked well.

Or, actually, this made me aware of another problem my system have...
When some of my Gaim contacts talk to my the text they are typing is transparent. You cant see it, even if you mark it.

Back a few days ago I removed the ms fonts I had pasted in /usr/share/fonts.

Is it possible that I have removed other systemt fonts, so gaim and other applications turns text with this font into transparent?

I did not have this problem before I tried to "install" these msfonts.

Am sorry, am going waaaay oftopic with his post :)

---

