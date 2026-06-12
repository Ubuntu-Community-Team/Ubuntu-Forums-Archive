---
title: "Broken emacs!"
date: 2005-11-06
forum: Desktop Environments
---

### Post by Jujimufu on 2005-11-06
My emacs is broken! Borked, forked, toasted! :mad: Maybe it's a simple problem to solve, but I don't know, what the hell is this?!  Here is a screen shot - there are no fonts - just boxes : /  Please save my GNU!

[img]http://www.trickstutorials.com/temporary/emacsbroken.gif[/img]

---

### Post by Jujimufu on 2005-11-07
?

---

### Post by bjourne on 2005-11-07
It has something to do with character encoding. Try this in a shell:

rm ~/.emacs

and restart emacs. Hope that helps.

---

### Post by will103 on 2005-11-08
Jujimufu,

I have the same problem and have been working on it for a while now. I seem to have fixed it on my machine, although emacs still returns a font error to the terminal.

Create an .Xresources file in your home directory and add the following line;

emacs.font: *fixed-bold-r-*-15-*-*

Then you should reboot your machine (or restart the X server).

I did not come up with this myself but came across it at the LinuxQuestions forums, under a question regarding a broken x.org installation.

Hope this sorts you out.

Will103

---

