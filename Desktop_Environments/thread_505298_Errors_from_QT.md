---
title: "Errors from QT"
date: 2007-07-20
forum: Desktop Environments
---

### Post by hylkedonker on 2007-07-20
Hello,
I wanted to pick up a project, I haven't been working on for a while.
After fixing a few syntax-errors, it compiled fine. When I ran my program I got the following output in my console:
> X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
failed rendering glyph 32 from font
ASSERT: "!err" in opengl/qgl_x11.cpp (888)
failed rendering glyph 160 from font
ASSERT: "!err" in opengl/qgl_x11.cpp (888)

I instantly recognized the first errors, because I get those errors from a lot of KDE programs, and since my program uses QT 3, I think it has to do with QT 3.
For example, if I run quanta, I get simmilar errors:
> hylke@hylke-ubuntu:~/dev-department/curve/testing/observer_pattern$ quanta
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
The errors from my program below the top errors, probably have to do with a function I use. I use the function QGLWidget::renderText to draw text to my QGLWidget. Maybe Ubuntu forgot to install some fonts?
Before I used Ubuntu, I used Slackware, and that's where I programmed most of my project on. I've never had any errors on Slackware, so it is Ubuntu related.
Can anyone help me fix these errors?
Thanks in advance,
Hylke

---

### Post by Happy_Man on 2007-07-20
Your first error is not due to QT, but due to xorg.conf settings. To fix it, comment out the wacom entries in xorg.conf.

The other errors are for you to fix, since we weren't the ones coding it.

---

### Post by hylkedonker on 2007-07-20
That indeed fixed the KDE-apps errors. Thanks a lot.
I'Il try to figure out the other errors(and the fact that Frame Buffer Objects don't seem to work).
Hylke

---

