---
title: "2 questions : restraint packaged and Firestarter"
date: 2006-07-07
forum: Desktop Environments
---

### Post by Paradoxx on 2006-07-07
Hi... I've been dual booting Ubuntu on my labtop for sometime now, and like it quite much, but I'm still pretty new to Linux.

My first question regards a packaged that has been restraint for a long time now. The name of the packaged is : gdk-imlib1 

What can i do to solve this ?

The second question is about Firestarter and how to avoid typing the password on startup . I've read on the Firestarter HP that i need to edit the file ”sudoers”. 
I did that and added the line: jonas ALL= NOPASSWD: /usr/bin/firestarter

however i realized that i was supposed say sbin instead of bin... but when i try to edit the line with gedit

code: sudo gedit /etc/sudoers

but i can't save the file ??

I hope you can help

---

### Post by pchr on 2006-07-12
It says at the top of the file that you should only edit it with visudo.  So in a terminal type:
```
sudo visudo
```

It then opens in nano which I've never used before, but isn't difficult, at the end when you exit it notice that it suggests saving the file as sudoers.tmp, the .tmp needs to be deleted if it's all going to be worth while.

I did this, but then when I tried to open firestarter I get a "Starting Firestarter" box in my window list, which then disappears.  Firestarter doesn't open.  I haven't got a clue why this is? :-k

---

