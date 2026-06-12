---
title: "Multiple Display Managers on different virtual terminals?"
date: 2005-10-25
forum: Desktop Environments
---

### Post by rychieb on 2005-10-25
I'm currently running kubuntu with kdm, and have X display :0 on virtual terminal 7.  My work involves demonstrating software and so i would like to run a separate instance of X (display :1) on virtual terminal 8.  This new display will run a single application in full screen mode using xdm so that i can quickly swap between the two as neccessary.

I've done this before on other linux distros, but any ideas on how to do this in *buntu?

Cheers

---

### Post by cwaldbieser on 2005-10-25
[QUOTE=rychieb]I'm currently running kubuntu with kdm, and have X display :0 on virtual terminal 7.  My work involves demonstrating software and so i would like to run a separate instance of X (display :1) on virtual terminal 8.  This new display will run a single application in full screen mode using xdm so that i can quickly swap between the two as neccessary.

I've done this before on other linux distros, but any ideas on how to do this in *buntu?

Cheers[/QUOTE]
I think you can just
```

$ startx -display :1

```

I like to use Xnest, myself:
```

#Start an Xnest server on display 1
$ Xnest -ac :1

#Start an xterm on display 1
$ xterm -display :1

#Start xfce4 on display 1
$ xfce4-session -display :1

#Start gnome on display 1
$ env -u SESSION_MANAGER gnome-session --display :1

```

---

### Post by cronosxfiles on 2007-12-21
Hello rychieb, 

  Have you tried cwaldbieser's suggestions? 

  I think I'm after the same thing, on my Ubuntu system - gdm. Having a second desktop environment available for showing a virtual machine on full screen mode with a different OS. 

  I've tried this:

```
  $ env -u SESSION_MANAGER gnome-session --display :1 
```

  but I'm getting an error saying (sorry, no textual message available now) something like: "[COLOR="Red"]can't find display 1[/COLOR]". Same thing when trying with display 2 or 3. I'm actually very ignorant of what this command is doing so, if you've managed to solve this, I'd appreciate a feedback on your experience. 

  Thanks. Regards, JM

---

