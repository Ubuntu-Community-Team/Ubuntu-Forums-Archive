---
title: "how to tell GNOME to use esound on another machine ?"
date: 2005-03-17
forum: Desktop Environments
---

### Post by garyng on 2005-03-17
My limited reading about gnome(on ubuntu at least) is that it can output to the esound daemon running on the same machine. Are there anyway to tell it to output to another esd daemon on another machine(I am VNC into it).

---

### Post by bored2k on 2005-03-17
[QUOTE=garyng]My limited reading about gnome(on ubuntu at least) is that it can output to the esound daemon running on the same machine. Are there anyway to tell it to output to another esd daemon on another machine(I am VNC into it).[/QUOTE]
 What about gstreamer-properties? [gui]

---

### Post by garyng on 2005-03-18
Don't quite understand what you mean ? Do you mean the pariticular app gstreamer ? What I meant was say the event sound under GNOME, can the be output to esound(but not the local esd) ?

BTW, I don't find gstreamer from the menu. 

Still learning.

---

### Post by bored2k on 2005-03-18
[QUOTE=garyng]Don't quite understand what you mean ? Do you mean the pariticular app gstreamer ? What I meant was say the event sound under GNOME, can the be output to esound(but not the local esd) ?

BTW, I don't find gstreamer from the menu. 

Still learning.[/QUOTE]
 from a terminal in the other pc
systems > administrations > multimedia systems
that is gstreamer-properties [that command is to run it through terminal]

---

### Post by garyng on 2005-03-18
I am sorry, I am even more confused. May be it is easier to explain what I have first.

Machine A - esound daemon listening on tcp port 16001
Machine B - ubuntu with GNOME 2.6.10(hoary)

I use VNC from A to B. Now for a esd enabled application, I believe it can be tell to use esound as the sound output by setting ESPEAKER=host:port in the environment.

What I want to do is tell GNOME on machine B to do exactly this. On B, I can only see under GNOME menu of System->Preferences->Multimedia System Selector. It is already using esd but this I assume is just a local daemon sitting on top of the local DSPs(so esd becomes a mixer for local device).

EDIT: Now I know why. I need to set ESPEAKER before launching GNOME.

---

