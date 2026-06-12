---
title: "Changing screen res"
date: 2007-04-13
forum: Desktop Effects &amp; Customization
---

### Post by JohnnyQuickCash on 2007-04-13
Im running feisty and cannot change the res to 1680 1050. Is there a way to do this manually? And how do I go about it?

---

### Post by xopher on 2007-04-14
What does your xorg.conf look like? You should add the resolution there manually if it's not automatically detected.

```
gksudo gedit /etc/X11/xorg.conf
```

If you're using NVIDIA, try setting the resolution with *nvidia-settings*

---

### Post by tdmoore on 2007-12-26
> **xopher said:**
> What does your xorg.conf look like? You should add the resolution there manually if it's not automatically detected.

```
gksudo gedit /etc/X11/xorg.conf
```

If you're using NVIDIA, try setting the resolution with *nvidia-settings*

As a newb to Ubuntu and still very confused by the command lines, would like to ask for assistance with similar issue.

For some reason that I can't figure out, my screen resolution will not go higher than 800x600, although my monitor will handle higher.  Have read through a lot of the forum posts and the instructions here are all associated with command prompts...and although I can copy and paste, the issue for me is HOW TO ACTUALLY MAKE THE CHANGE in the terminal window.

I have tried Add/Remove and installed some of the graphic card drivers however max resolution I see is 800 x 600 and the only other option is 640 x 480.

Can someone assist me with this please so I can get to a better resolution?

Running 7.10 Gutsy, monitor is a LG Flatron LCD 563LE.

Appreciate any help here as the forum groups have been good to me in the past.

---

### Post by tdmoore on 2007-12-26
> **tdmoore said:**
> As a newb to Ubuntu and still very confused by the command lines, would like to ask for assistance with similar issue.

For some reason that I can't figure out, my screen resolution will not go higher than 800x600, although my monitor will handle higher.  Have read through a lot of the forum posts and the instructions here are all associated with command prompts...and although I can copy and paste, the issue for me is HOW TO ACTUALLY MAKE THE CHANGE in the terminal window.

I have tried Add/Remove and installed some of the graphic card drivers however max resolution I see is 800 x 600 and the only other option is 640 x 480.

Can someone assist me with this please so I can get to a better resolution?

Running 7.10 Gutsy, monitor is a LG Flatron LCD 563LE.

Appreciate any help here as the forum groups have been good to me in the past.
[SOLVED] - not sure why, but power went out and when computer rebooted it changed resolution to 1024 x 768....unbelievable luck.

However, I now have a small sliver of black down the left and even though have tried to use the monitor controls, this is as far as I can get it.  Now asking for help on that.

Thanks again for help in advance and for patience with us Newbs!

---

