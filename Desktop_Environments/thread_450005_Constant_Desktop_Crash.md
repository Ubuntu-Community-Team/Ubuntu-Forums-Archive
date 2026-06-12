---
title: "Constant Desktop Crash"
date: 2007-05-20
forum: Desktop Environments
---

### Post by Eric the Red on 2007-05-20
My desktop has been crashing while in Ubuntu. Its really weird because it only happens when I press a certain combination of keys. 

At first, when my desktop crashed and went out of Beryl, I entered my user name and password (for a second time) and when back into Ubuntu but with Gnome this time. Unfortunately it crashed in gnome with the same problem as in Beryl. The pain to this is that every time the desktop crashes I lose all applications that were open. 

I did press a variety of keys to test the issue and I found out that the combination of "Shift + backspace" causes the desktop crashes. There's probably a few more but I'll post other combos if I find them. 

The first thing I tried was that I started the Gnome manager in safe mode (without the startup scripts) and the crashes didn't occur with Shift + Backspace. 

Does anyone know of a way I could investigate to see what script is grabbing those keystrokes and crashing?? I'm completely out of ideas so any help would be appreciated.

---

### Post by Rmorris84 on 2007-05-21
Shift+Backspace isnt crashing your computer... its restarting your X (display). Which intern, makes you have to log back in. Perfectly normal. Im sure you can change it/disable it.

---

