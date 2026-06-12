---
title: "Which scripts are sourced at login?"
date: 2005-12-06
forum: Desktop Environments
---

### Post by entner on 2005-12-06
Hello Ubuntuers!

I just recently read in ubuntu-users mailinglist that the ~/.gnomerc script is sourced at Gnome-login.

I have a ~/.profile, ~/.bashrc which are sourced depending if I just start a new Bash or login via SSH.  It seems that none of them is sourced at the Gnome login.

Is there a general explaination which scripts are sourced (if they exist) when I log into a default Ubuntu Gnome session? I am confused where to put my aliases, the PATH and PS1 environment or my fortune.

Thanks,
Burt

---

### Post by hw-tph on 2005-12-06
While I don't know if this is the "Gnome way" of doing I have also done it this way and it works well enough for me:

Make sure your ~/.bash_profile sources ~/.bashrc:```
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi
```

Set the Gnome Terminal to always execute as a login shell and that's it - put your aliases anywhere you like. I have a ~/.bash_aliases sourced from ~/.bashrc (which in turn is sourced from ~/.bash_profile...) to keep my aliases separated from other stuff.

If you're like me and don't like the bulky slow Gnome Terminal and use rxvt-unicode or something similar instead you can set up your ~/.Xdefaults to make your terminal a login shell at all times:```
urxvt*loginShell: True
```
Substitute urxvt with aterm, rxvt or whatever terminal app you run.

Like I said, this is probably not the Gnome/Ubuntu way of doing it but it works for me. :)


Håkan

---

