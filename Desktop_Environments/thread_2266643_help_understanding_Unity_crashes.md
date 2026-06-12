---
title: "help understanding Unity crashes?"
date: 2015-02-24
forum: Desktop Environments
---

### Post by Allen McBride on 2015-02-24
I'm running Ubuntu 14.10 on a Dell Inspiron 7737. It usually wakes up from sleep successfully, but often instead of the lock/login screen, I see what was on the screen when it went to sleep, but frozen except that I can move the mouse cursor. I can get to the console with Ctrl-Alt-Fn, and from other threads, I've gleaned several things to try from there:
[LIST]
[*]nohup setsid unity
[*]nohup unity --restart
[*]nohup compiz --replace
[*]unity &> /dev/null & disown
[*]compiz --display :0 --replace & disown
[*]nohup compiz --display :0 --replace &
[*]Alt-F2 and then "unity" (this one from the graphical console)
[/LIST]
...every now and then some combination of these will work, but usually none do. And when they do work, I lose the menu bar (or whatever the icons at the upper-right are called in Unity). sudo service lightdm restart always works, but it kills my programs.

Any advice about what's causing this or other suggestions for fixing it? I'm having other problems too, like the fact that encrypted swap isn't working at all, although I haven't done a lot to try to fix that yet. Would I be better off reformatting my hard drive and reinstalling, perhaps without a Windows partition like I have now?

Thanks!

---

