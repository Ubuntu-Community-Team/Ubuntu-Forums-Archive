---
title: "3 Questions: Startup, AmaroK, Kontact backup"
date: 2005-08-23
forum: Desktop Environments
---

### Post by alquimista on 2005-08-23
Hi,

After another interesting week discovering Linux/Kubuntu, I have 3 questions:

1- How can setup my Kubuntu system so on startup some programs get executed automatically, like an autoexec.bat?  Or “Startup” in Windows? 

2- When in  amaroK I wanted to play an audio CD (original, not mp3) (Actions -> Play audio cd), I get the following error:
“Could not start process  Unable to create io-slave: klauncher said: unkown protocol audiocd”. I have xine as engine, and amaroK is version 1.2.3 on KDE 3.4.2, Using Kaffeine I have no problem listening audio CDs.
How can I fix it?

3- How can I backup all Kontact data? Calendar, mail, contatcs, etc. Is there a directory I can zip and backup?


Thank you very much,
Guillermo

---

### Post by Freddy on 2005-08-23
I can answer your first question. 

Put the executable program file in /home/username/.kde/Autostart and restart your KDE. 

The second question I'm unsure with, but with the gstreamer which I use, you can download gstreamer-audiofile plugin which should do the trick. Don't use xine engine though, so with that I'm not sure.  /// Freddan

---

### Post by beefsprocket on 2005-08-23
[QUOTE=alquimista]3- How can I backup all Kontact data? Calendar, mail, contatcs, etc. Is there a directory I can zip and backup?[/QUOTE]

Is there a .kontact or .kde/share/apps/kontact directory in your home folder?

---

### Post by alquimista on 2005-08-23
Yes,
There is a Kontact directory, bu its empty; I found a KMail directory I suppose I can back it up. Yet I have to see if there is another one for contacts, calendar, etc.

Thank you,
Guillermo

---

