---
title: "totem (gstreamer) codecs"
date: 2005-10-15
forum: Desktop Environments
---

### Post by gila_monster on 2005-10-15
Okay, I realize that this question has come up before, and I've read the pertinent posts on it, but I'm still having problems, so bear with me.

I cannot seem to get totem to recognize codecs. I can't play mp3s, I couldn't play a DVD I tried (it was My Little Pony, so perhaps just as well). I have tried putting the mplayer "essential codecs" in ~/.gnome2/totem-addons and in /usr/lib/win32, but totem insists it has no codecs for common file types.

What am I missing? What am I doing wrong?

Apologies if I'm missing something simple. I tend to have problems with the easy stuff, but someone I work through the hard stuff. :)

Gila

---

### Post by F for Fragging on 2005-10-15
Did you install gstreamer0.8-pitfdll (also added repositories)? Tried entering gst-register (or something, dunno again what it exactly was) in the terminal, after having the codecs and pitfdll installed?

I hope Ubuntu Guide will get updated to Breezy soon, should answer most of everyone's problems and questions.

---

### Post by KrazyPenguin on 2005-10-15
Installed all the codecs, and  tried gstreamer0.8-pitfdll and gst-register-0.8 and everything installed oK and I still can't get a mpeg file to play on totem :( 

What am I missing??

---

### Post by F for Fragging on 2005-10-15
Well, maybe the best solution will be to install totem-xine which uses Xine instead of Gstreamer. I also have problems with Gstreamer, Xine does play everything for me. Gstreamer is probably still buggy.

---

### Post by KrazyPenguin on 2005-10-15
Installing totem-xine removed totem-gstreamer but guess what??

IT WORKS!!!!

:D

---

### Post by gila_monster on 2005-10-15
[QUOTE=F for Fragging]Did you install gstreamer0.8-pitfdll (also added repositories)? Tried entering gst-register (or something, dunno again what it exactly was) in the terminal, after having the codecs and pitfdll installed?

I hope Ubuntu Guide will get updated to Breezy soon, should answer most of everyone's problems and questions.[/QUOTE]

That helped! Thanks.

Gila

---

### Post by fmcdee on 2005-12-10
I have downloaded and installed the codec I need, .  I need to register the codecs at the command line.  Where is the command line, or how do I get to it?? Thanks.:)

---

### Post by cwaldbieser on 2005-12-11
[QUOTE=fmcdee]I have downloaded and installed the codec I need, .  I need to register the codecs at the command line.  Where is the command line, or how do I get to it?? Thanks.:)[/QUOTE]
If you go to Applications -> Accessories -> terminal, you will get a program that looks like a black rectangle that has a "$" prompt that you can type stuff at.  It might remind you of how MS-DOS looked.  That is the command line.

---

