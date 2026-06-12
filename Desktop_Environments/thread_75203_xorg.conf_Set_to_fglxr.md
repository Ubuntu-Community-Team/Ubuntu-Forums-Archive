---
title: "xorg.conf Set to fglxr"
date: 2005-10-13
forum: Desktop Environments
---

### Post by MuRRe on 2005-10-13
I did it... LOL
I installed a driver and changed the xorg.conf. Luckily i have a backup named:
xorg.conf_backup

I cannot log into Gnome so i have to do it the hardcore way.
How do i remove the old xorg.conf
and then rename the xorg.conf_backup?

---

### Post by Karasu Tengu on 2005-10-13
rm /etc/X11/xorg.conf
cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

---

### Post by MuRRe on 2005-10-13
THANKS. It works again. What "program" can u use in "dos" enviorment to edit text-files...?

---

### Post by Karasu Tengu on 2005-10-13
by DOS you must meen terminal :)

use nano (easy)
use vi (un-freandly but its the one I use)

nano -> ctrl-o to overwrite
nano -> ctrl-x to quit

vi -> i to insert text
vi -> esc to stop editing
vi -> :wq! to write/quit/!= no prompt

---

### Post by drogoh on 2005-10-13
[QUOTE=Karasu Tengu]by DOS you must meen terminal :)

use nano (easy)
use vi (un-freandly but its the one I use)

nano -> ctrl-o to overwrite
nano -> ctrl-x to quit

vi -> i to insert text
vi -> esc to stop editing
vi -> :wq! to write/quit/!= no prompt[/QUOTE]

aee or 'ee' is another one.  It's a lot easier to manipulate than nano/pico.

---

### Post by matthias_k on 2005-10-13
[QUOTE=MuRRe]THANKS. It works again. What "program" can u use in "dos" enviorment to edit text-files...?[/QUOTE]
Stop thinking Windows. :) What you mean is the command line shell, or some terminal program running a shell. To answer your question: Many. To check which text editors are available in the repositories you have linked, try this: ```
$ aptitude search ~d'text editor'
```
Or this, if aptitude is not installed: ```
apt-cache search 'text editor'
```
This will list all packages which have "text editor" in their description.

By the way, there is a pretty decent beginner guide to Linux on [www.tldp.org](www.tldp.org). Read that, it will answer a lot of your questions.

---

### Post by Olav on 2005-10-13
[QUOTE=drogoh]aee or 'ee' is another one.  It's a lot easier to manipulate than nano/pico.[/QUOTE]
Right. But nano and pico are installed in Ubuntu per default, so that' s what you recommend when someone needs a console editor quick. And they are not difficult to operate at all ;)

---

### Post by dcarpenter on 2005-10-13
i noticed in the title of this thread you spelled FGLRX wrong.. did u do this in your xorg.conf??  If so, fix it! :)

---

