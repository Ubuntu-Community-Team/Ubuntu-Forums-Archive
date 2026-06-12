---
title: "Change tty fonts"
date: 2009-01-04
forum: Desktop Environments
---

### Post by lancest on 2009-01-04
How do i change my tty fonts? I have wanted to change this for some time. Tried these:

[http://ubuntuforums.org/showthread.php?t=227513](http://ubuntuforums.org/showthread.php?t=227513)
[http://phaselockfel.blogspot.com/2007/09/change-tty-terminal-font-size.html](http://phaselockfel.blogspot.com/2007/09/change-tty-terminal-font-size.html)
[http://ubuntuforums.org/showthread.php?t=258484](http://ubuntuforums.org/showthread.php?t=258484)

Nothing works!  Using Nvidia 7300 on 8.10 
For example I really prefer the tty's on SuSE or Slackware.

---

### Post by DefineByte on 2009-01-04
Try ```
setfont foo
``` where foo is a font found in */usr/share/consolefonts/*.

e.g. ```
setfont Uni3-TerminusBold24x12
```

You can put the command in *~/.bash_profile* if you want it to stick.

---

### Post by xcesarfrancox on 2009-03-27
How can it be done systemwide?

I mean, to be changed before the user logs in

---

### Post by DefineByte on 2009-03-30
Does [this thread](http://ubuntuforums.org/showthread.php?t=329369) offer what you're looking for?

---

### Post by xcesarfrancox on 2009-03-30
Yes thank you very much :)

---

