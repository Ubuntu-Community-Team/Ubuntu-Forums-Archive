---
title: "aticonfig broke X"
date: 2008-05-13
forum: Desktop Environments
---

### Post by wxs on 2008-05-13
Hi all,

I've just installed Ubuntu for the first time, and I have a dual screen setup with an ATI graphics card. In order to set up an extended desktop I used the following command

```
sudo aticonfig --initial=dual-head --screen-layout=above
```

as shown in the help file for aticonfig. After restarting, this *almost* worked, in that I now have an extended desktop and can move my mouse between both screens. Unfortunately it seems to have messed up the window manager.

Now when I open any program it opens up at the top-left corner of the screen in which I opened it. I can't move the window since the handle is either off the screen or doesn't even exist (not sure which). In addition to this, keyboard focus seems to lock in to that window. For example at the moment I have Firefox open on one display and a terminal window open in the other. Although I can click on the menus of the terminal window, I am unable to type to it. If I want to type in there I have to close both Firefox and the terminal, and then open a new terminal window.

My best guess is that aticonfig screwed up xorg.conf, I could always revert to my backed up version, but then I wouldn't have extended desktop.

Any ideas?

---

### Post by wxs on 2008-05-13
Okay, I have no idea how this worked, but it seems to have (and is a lot simpler than all the other solutions I've seen on the web). Basically I decided that I'd just switch back to mirroring since it would be easier than getting an extended desktop. I reverted my xorg.conf file to the backed up version that I'd had *before* running the initial-setup command and somehow I now have a working extended desktop. I haven't the slightest idea why though...

---

