---
title: "Window decorator manually only :("
date: 2009-12-27
forum: Desktop Environments
---

### Post by jessmanboo22 on 2009-12-27
Hello World!

Recently I tried out Emerald. Excellent, very neat what you can all do with it.
I decided to make my own theme with it, so in the meantime I just want my regular Ubuntu theme. When Igot it I applied the default theme that comes with Emerald (I found out how on the internet: the way I learned was terminal: "emerald --replace". I know there is some GUI way to do it too but I don't understand that.

Anyway, after accidentally making the X button on my windows 1px wide (who knows what the heck I was doing?) and then saving because I forgot I had messed with the X, it applied and now my X's are only 1px wide and they are extremely annoying. I wanted to switch back to Metacity so in the terminal I went "gtk-window-decorator --replace". (Again, I found out to do this on the internet.) I was satisfied with having the good ol' normal back, so I closed the terminHEY!     What happened?     my... my title bars! Th... They're gone! After I closed the terminal, I lost my title bars of all of my windows. I right click their buttons in the Windows list to move, maximize, etc. Now I only get a window decorator if I type "<program> --replace" in the terminal, and if I close the terminal, they go away again! What did I do wrong and how can I make the gtk-window-decorator come on automatically again? Please help, reps (and great gratitude) to all those who can help me!

~Jessmanboo

P.S. I'm mostly booting on Winblows XP until I can fix this problem because it's a bit too annoying. I always accidentally close the terminal, and for five minutes I can't remember the solution to the disappearing title bars :(

---

### Post by ST3ALTHPSYCH0 on 2009-12-28
It looks like metacity will automatically take back over if you set visual effects to none.
[Click for more details](https://help.ubuntu.com/community/Metacity)

---

### Post by PsychoDevon on 2009-12-28
Aaah, I just recently learned how to fix that.

See, to the best of my knowledge, when you use --replace, you're essentially changing the way your window decorator is handling your windows. The bad thing about using it in terminal is that then it will run as a command, and you must keep the terminal window open in order to handle your windows using Emerald, metacity, etc.

You have two options.

1) For a fix right now, press alt+f2 and type in "/usr/bin/compiz-decorator --replace" (no quotes) and edit the theme in Emerald Theme Manager like you were before, and fix the close button.

*The reason I told you to use alt+f2 instead of a terminal is that if you put in the --replace command in the alt+f2 prompt, it automatically closes so you don't have to worry about un-executing the command in a terminal when you close it.

2) after doing that, go into CompizConfig Advanced Settings Manager, and go to the Window Decoration tab. If you want to use emerald, in the  "Command" section, type in emerald --replace. If you want to use Metacity, type in /usr/bin/compiz-decorator --replace. This will start either Window Decorator at startup, so you don't have to worry about that pesky prompt, or --replace command in terminal.

---

### Post by jessmanboo22 on 2009-12-28
Terrific! I just hit "None", and then hit "Extra", waited for the driver search, and it's fine! Why didn't I even think to look at the Metacity page...

Oh well, thanks sooo much for helping me get it normal again! Now I'll work on that theme...

EDIT: Ok, thanks PsychoDevon! I still have a bit to understand about the window decorators and other "extra-curricular" stuff that runs on Ubuntu to make it what it is. It's interesting to take a browse through System Monitor. I'm an Ubuntu proselyte from Windows XP, and I think it's neat how Ubuntu, being Linux, open source, or whatever, is so much more customizable and... open! It's not all one program like explorer.exe or whatever, where it's all... uh.... "closed"... LOL. Thanks!

EDIT2: Is there a such thing as reps on this forum??

Reps! :)
~Jessmanboo

---

