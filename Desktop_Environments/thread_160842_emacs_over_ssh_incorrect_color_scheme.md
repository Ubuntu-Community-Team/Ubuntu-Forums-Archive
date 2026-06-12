---
title: "emacs over ssh: incorrect color scheme"
date: 2006-04-15
forum: Desktop Environments
---

### Post by jsweds on 2006-04-15
For schoolwork, I often ssh into a Solaris machine.  When I run emacs, the color scheme is not correct.  The text colors are correct, but instead of a black background, I get the background color from my local Gnome theme.  Is there some way to fix that?

---

### Post by art on 2006-04-16
Is it black when you login to that machine sitting in front of it? All the settings for emacs are stored in the ~/.emacs file (on the host machine, Solaris in this case), so tweak that to your liking.

---

### Post by jsweds on 2006-04-16
Yes, it is black when I run it on the Solaris machine.  I copied that .emacs file to my Ubuntu machine, and the colors come out correctly when running it locally.  The color scheme is also correct when I ssh from Windows using SecureCRT and Cygwin/X.

---

