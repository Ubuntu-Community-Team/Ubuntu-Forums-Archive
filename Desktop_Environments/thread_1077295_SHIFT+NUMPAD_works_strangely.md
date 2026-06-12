---
title: "SHIFT+NUMPAD works strangely"
date: 2009-02-22
forum: Desktop Environments
---

### Post by [Po]lentino on 2009-02-22
Hi all,
I've decide to open this thread because of a buggy behaviour happening with numpad on my laptop.
As you can see on the title, I'm using Kubuntu Jaunty Alpha4; but, after you tell me *"Bugs are normal with development branches,try the stable version"*, I have to advise you that I always tried other development version of Ubuntu, and the problem arises only with KDE... With Gnome, all worked fine.

So let's move on the problem:
My keyboard layout is a Generic 104 keyboard;  numpad contains numbers ( of course :P ) and also the arrow keys, mapped as follow:
*UP_ARROW* in the *"8"* key, *DOWN_ARROW* in the *"5"*, *PAGE_UP* on the *"9"*, *PAGE_DOWN* on the *"3"*, and so on ...

When *NUM_LOCK* is off, KDE interprets the keys pressed as arrow keys, that's fine.
But when I hold *SHIFT*, whatever key I press ( because the action I want to perform is selecting a text ), i get the corresponding number printed out instead of the desired selection. So, now I can surf on the text, display numbers, but I cant select text.
If I turn on *NUM_LOCK*, now the numbers are displayed and, if I HOLD the *SHIFT* key, now I can select the text I want. So, now I can display number, select text, but I can't surf the document.

The practical issue is this:
If I have a source code ( or whatever document ) to edit, so I scroll the page with *PAGE_UP* or *PAGE_DOWN* ( with the *NUM_LOCK* off ) , I move to the desired location with the arrow keys; now I should select the text, but if I hold on *SHIFT* and then press *LEFT* or *RIGHT* key, it appears *4* or *5* accordingly with what I said after...
So I have to turn on *NUM_LOCK*, now press *SHIFT*, copy/cut/delete the desired text, and if I want to come back to the original position, I have to use the arrow keys again so I have to turn off again *NUM_LOCK* ...
And I have to repeat this procedure every time ...
What an annoyig one :(

So, anyone knows how to fix this small bug ??

Under Gnome, I remember a *Keyboard Layout* applet, and a tab called *"MS behaviour"* where you can enable a property called *"SHIFT+NUMPAD works like microsoft keys"*, or somethig similar; but I cant find something analogous in KDE :(

---

### Post by [Po]lentino on 2009-02-22
Any suggestion ?

---

### Post by Clever_Username on 2010-06-30
bump

---

### Post by pethal75 on 2010-09-26
I have searched for this also and here is solution in keyboard preferencies layout options

[https://help.ubuntu.com/7.04/user-guide/C/prefs-hardware.html](https://help.ubuntu.com/7.04/user-guide/C/prefs-hardware.html)

there is option 

                                   *Miscellaneous compatibility options*                                                                                                                    *Shift with numpad keys works as in MS Windows.*

---

### Post by Chame_Wizard on 2010-09-26
I really don't have a problem at all here.


*USA keyboard layout with €-sign *

---

### Post by reuben on 2010-12-19
Settings - Input Devices - Keyboard - Advanced - Misc Compatibility Options - Shift with numeric keypad works like MS Windows

It's a lame default, but at least the option is there.

---

### Post by davidsarah on 2011-03-21
The location of this option in Gnome has changed a bit, so here's an  updated description of how to set it for anyone googling this. Note that  this is only for Gnome; I don't know the answer to the original  question about KDE.

Go to System | Preferences | Keyboard, click the Layouts tab, click  Options..., expand 'Miscellaneous compatibility options', and check **both**  "Shift does not cancel NumLock, chooses 3rd level instead" and "Shift  with numeric keypad keys works as in MS Windows". Click Close. You'll  probably want to apply this change system-wide, so click that button and  authenticate. Also make sure that 'Pointer can be controlled using the  keypad' is **not** checked under the 'Mouse Keys' tab.

---

