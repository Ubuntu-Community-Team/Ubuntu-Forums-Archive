---
title: "Gutsy Compiz Fusion Nvidia problems"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by bobulator on 2007-10-25
I am a user of Gutsy gibbon and I am trying to install Compiz Fusion.
My graphics card is a Nvidia GeForce 4 MX 440.

Firstly, I have installed xserver-xgl -- is this what I should do?

Secondly, I tried selecting Compiz desktop Effects in the 'Appearance Preferences' but when I do so, the screen goes white.

I also typed 'compiz --replace' in the terminal which also caused the screen to white out. Is there a compiz log file so that I can see what the problem is?

Thanks in advance
:)

---

### Post by Tanker Bob on 2007-10-25
I recommend installing and using the latest version of Envy to install the proprietary NVidia driver for your card.

---

### Post by bobulator on 2007-10-26
I have installed the latset Nvidia driver using Envy and restarted.

Now when I select Desktop Effects in the 'Appearance' control module a prompt appears saying I should re-activate the proprietry nvidia (i.e. Non-Envy) driver. 
Should I do that or is there a work-around?

---

### Post by judolars on 2007-10-26
Have you tried *not* using xserver-xgl?

Although I have to admit I don't really know what said package does, I can tell you this: I have a relatively new nVidia card, I am using just the ordinary X.org server with the nvidia-glx-new driver package and everything works like a charm -- Compiz too.

---

### Post by Steve1961 on 2007-10-26
You don't need the xgl package with nvidia cards.

---

### Post by bobulator on 2007-10-26
Thanks, I should use AIGLX then.

:)

---

### Post by Steve1961 on 2007-10-26
> **bobulator said:**
> Thanks, I should use AIGLX then.

:)

Yes, that's what I'd suggest

---

### Post by bobulator on 2007-10-27
UPDATE::

I've reinstalled ubuntu 7.10.
I then installed Envy and dloaded the latest Nvidia Drivers.

And it works!

---

### Post by Steve1961 on 2007-10-27
Glad you've got it sorted out :)

---

### Post by Stank0 on 2007-10-29
I have nVidiaGO 7900GLX and when I run Compiz without xgl it will inevitably freeze up sooner rather than later.
I tried it with the proprietary driver from Gutsy's repositories and now I'm running adriver installed by Envy.
So far no freez-ups (when xgl runs). 
Oh and I'm running KDE if that matters at all.
What I read everywhere I'm supposed to run Compiz without xgl but how to make it run so it won't freeze up on me?

I'd be ok with xgl but I can't use the pressure feature of my Wacom Graphire4 tablet in Gimp under xgl.
And there are quite a few other quirks. While minor, they are annoying as hell.
Without xgl everything works great. Except for Compiz though. :(

---

