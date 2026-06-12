---
title: "How to Access my old saves with VBA-M?"
date: 2012-01-16
forum: Emulators
---

### Post by ReticentGrace on 2012-01-16
Recently switched back to linux (about two hours ago!), and now I have questions. I hope this is the right place for them.

Upon looking through the forums I noted that VBA-M was being recommended for playing GBA games over visual boy advance, but I'm transferring my games and my save files from my other partition...which means that my save files were made in Windows XP. 

They're marked as **.sgm** and** .sav** ; it doesn't appear to recognize that they exist. Is there any way to convert them or tell the VBA-M to read them? An option I have to click, or some such other thing? I know that it's a silly question, but I'm hoping to figure something out.

Mistakes can be frustrating- even simple ones! :KS

Thanks in advance for any answers anyone shoots my way.

---

### Post by brencameron on 2012-01-28
I don't know if you figured it out yet, but most likely the emulator isn't looking in the place where you copied your .sav files to. By default, VBA-M seems to use the .config/gvbam/ folder in your home directory to store its saved  games. Try copying the .sav files that you want to play from into that folder and check again.
The other option is to change what directory VBA-M looks into for the save files, but I don't normally do that.

---

