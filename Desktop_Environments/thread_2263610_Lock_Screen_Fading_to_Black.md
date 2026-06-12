---
title: "Lock Screen Fading to Black"
date: 2015-02-02
forum: Desktop Environments
---

### Post by pineda-christopher98 on 2015-02-02
[B][FONT=comic sans ms][SIZE=4]The title say's it all, Everytime i do Lock my Screen (ctrl+alt+l) it makes my computer locked which it should but at the same time it makes my screen go fade slowly to black until my Monitor goes to sleep or idle. I need to move my mouse to make the screen go back. How you disable it? I don't like making my monitor idle, i just want to make my computer locked but not in black screen or something, is there anyway or atleast a trick on how to disable that thing? I want to have the same thing just like in Windows, You lock your screen in windows and it will not make your monitor fade to black. I know it's just a trick to do or something it's not a hardware problem or something, so i think i don't need to post my Specs here.. Thanks for answering in advance.!


BTW, im on 14.10 -64bit if that helps.
[/SIZE][/FONT][/B]

---

### Post by ajgreeny on 2015-02-02
Do you have a screensaver installed and configured?

I use xscreensaver, not because I need it but just as a way of viewing all my photos randomly after a few minutes of inactivity, and when I lock my screen that is what shows.

---

### Post by pineda-christopher98 on 2015-02-02
no i dont have any, i just reinstalled my 14.10 a week ago, i already experience this thing since 12.10, i know it's one of the feautures of ubuntu, but i want to disable it..

---

### Post by CantankRus on 2015-02-02
It looks to be part of the "**gnome-screensaver-command -l**" command and I don't see an easy way to disable it.
ie "gnome-screensaver-command -l" brings up the lock screen and also initiates the screen blanking.

Notice that initially when the lockscreen is activated it starts to dim almost immediately.
If you come out of the screen blanking by moving the mouse or hitting a key it will then 
activate screen blanking according to your brightness and lock setting.

---

### Post by pineda-christopher98 on 2015-02-02
Wow thanks for that, It worked on my Gaming PC and on my laptop should done that back when i still had the 12.10, worked for me, Thanks again, i'll mark this Thread as "SOLVED"

---

