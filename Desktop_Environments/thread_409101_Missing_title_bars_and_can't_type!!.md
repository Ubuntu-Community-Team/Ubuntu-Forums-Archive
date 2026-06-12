---
title: "Missing title bars and can't type!!"
date: 2007-04-14
forum: Desktop Environments
---

### Post by bootsbradford on 2007-04-14
I upgraded to feisty on thursday evening - no problems at all, worked fine!
Booted up yesterday (friday) morning - worked all day and absolutely fine!

Booted up yesterday (friday) evening, having jammed on boot-up the first time - big problems ever since...

   1. Basic problem is that all application windows are missing the top and bottom of them (e.g. minimising icon, exiting icon)
   2. My windows switcher icon has vanished and cannot be reloaded
   3. In many applications, e.g. firefox, xchat (though not all, e.g. open office) I cannot type anything!

This works is the case on all kernels in the boot-up menu. 

Problem #1 and #2 seem similar to [this thread]("http://ubuntuforums.org/showthread.php?t=406225") but can't see mention of problem #3, the inability to type/write text in some applications.

I really need some help - ubuntu is absolutely useless in this state at the moment!

---

### Post by Jerem on 2007-04-14
Do you use Beryl or Compiz ? If you do, select Metacity as window manager to see if these problems are resolved.

With Beryl I had the problems #1 and #3. The first one can be resolved with [a little change in xorg.conf]("http://forum.beryl-project.org/viewtopic.php?f=35&t=1631").
The #3 disappeared by itself, so I can't help you about this.

---

### Post by fsando on 2007-04-14
A simple way may be to reload the Window Decorator - I don't know why but sometimes it does not load: go to beryl manager menu select 'Reload Window Manager' usually this fixes it (also for the future).
And btw I believe title bars are still there they're just invisible - you can test if you can move windows by grabbing above the visible part of the window, and similarly access the buttons etc.

---

