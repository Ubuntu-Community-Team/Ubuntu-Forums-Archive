---
title: "How do I make X respect the contents of my ~/.xinitrc or ~/.Xclients-default file?"
date: 2006-06-14
forum: Desktop Environments
---

### Post by Derleth on 2006-06-14
I have a few programs I want to run every time I start X (xmodmap, xscreensaver, etc) and the natural place to put them seems to be either ~/.xinitrc or ~/.Xclients-default.

However, I'm coming from a long Red Hat and Fedora background. It seems Ubuntu is different in many key ways. One of those ways is that neither ~/.xinitrc nor ~/.Xclients-default is respected in the slightest.

How do I change that?

(BTW, I'm running Ubuntu but not GNOME. My windowmanager of choice is WindowMaker.)

---

### Post by Sutekh on 2006-06-14
Are you using a login manager?  Or or you starting WindowMaker from the command line?

If you are using a login manager, say GDM, when the default session is started it refers to the file ~/.xsession. You can make this use your ~/.xinitrc by sym-linking them
```
ln -s ~/.xinitrc ~/.xsession
``` 
If you are starting WindowMaker from the command line, are you using startx or somehing else?  *startx* should use just use your ~/.xinitrc.


You can get some more useful information on using ~/.xinitrc and ~/.xsession here

 [Ubuntu Wiki - Custom X Session]("https://wiki.ubuntu.com/CustomXSession")

---

### Post by Derleth on 2006-06-15
I'm currently using gdm because startx doesn't appear to work yet. I'm sure I'll get that sorted soon enough, however: It's doubless due to some cruft in $HOME left over from Fedora or Mandriva or some other distros I've used in the past few years on this machine. ($HOME is always its own partition, and it survives OS changes completely intact. Sometimes not entirely a good thing.)

Anyway, thank you for the tips. I'm sure that between them and my further research, I'll get all this sorted soon enough.

---

