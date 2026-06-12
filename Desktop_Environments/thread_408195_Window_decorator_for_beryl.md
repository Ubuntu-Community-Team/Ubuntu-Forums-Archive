---
title: "Window decorator for beryl"
date: 2007-04-13
forum: Desktop Environments
---

### Post by siraf on 2007-04-13
Hey,

I've recently had to re-install ubuntu due to a massive failure on beryl loading up on entrance. [Feisty Fawn]

After the clean new install [edgy eft], I tried to reinstall beryl, it works -- sort of. I can't seem to move windows around, and there are no window borders. I can get compiz to work, but I like beryl a bit more. 
Other than the crash, I had NO problems before.

So I have two questions:

1. how can I get the window manager up and running again, with window borders?

2. how can I prevent this from happening again?

---

### Post by Neecapp on 2007-04-13
right click on beryl manager reload window manager

or you might have to select window manager > metacity
then select window manager > beryl

if that doesn't do it.. reload window decorator 

or select window decorator > gtk
select window decorator > emerald

Yep.

Every now and then it happens when you log in.. but those should fix it.. if not log out ctrl + alt + backspace

log back in...

---

### Post by Lykourgos on 2007-04-21
Also right click on Beryl Manager and 

Advanced Beryl Options->Rendering Path->Copy

This worked for me, hope it will work for you too

---

### Post by CameO73 on 2007-04-21
If you have a nVidia card, this is a known problem. Just edit your /etc/X11/xorg.conf and add some lines to your [Device] section (as mentioned [here](http://nlindblad.org/2007/01/28/no-window-borders-with-beryl-and-nvidia-aiglx/)). Especially the **AddARGBGLXVisuals** line is important in this case. Personnally I have this added to the [Screen] section ... that seems to work too :confused:

---

### Post by ethos101 on 2007-06-15
> **Lykourgos said:**
> Also right click on Beryl Manager and 

Advanced Beryl Options->Rendering Path->Copy

This worked for me, hope it will work for you too

Wow, I had it working in "auto" forever.  I was recently playing with an xfce session install and suddely lost window decoration.  I have absolutely NO idea what I did to lose it.

Anyways, this worked for me.  What exactly does the "copy" rendering path mean?

---

### Post by mikerouse on 2007-06-23
> **Lykourgos said:**
> Also right click on Beryl Manager and 

Advanced Beryl Options->Rendering Path->Copy

This worked for me, hope it will work for you too

This method worked for me to get my window title bar and borders back. Thanks Lykourgos!

---

### Post by cardiforia on 2007-06-23
oh yeah! Copy worx for me :D

Thanks a lot buddy :)

:popcorn:

---

### Post by rocknrolf77 on 2007-06-23
> **CameO73 said:**
> If you have a nVidia card, this is a known problem. Just edit your /etc/X11/xorg.conf and add some lines to your [Device] section (as mentioned [here](http://nlindblad.org/2007/01/28/no-window-borders-with-beryl-and-nvidia-aiglx/)). Especially the **AddARGBGLXVisuals** line is important in this case. Personnally I have this added to the [Screen] section ... that seems to work too :confused:


Use this tip instead. Copy just makes everything go slower ;)

---

