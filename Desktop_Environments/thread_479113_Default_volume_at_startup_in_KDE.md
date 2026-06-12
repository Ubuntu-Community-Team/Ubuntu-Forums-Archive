---
title: "Default volume at startup in KDE"
date: 2007-06-20
forum: Desktop Environments
---

### Post by clk99 on 2007-06-20
Whenever I boot up KDE, my volume is set to very low (not sure exactly, but something like 10%) and I have to change it to where I like it every time (100% ;)).  This is hardly an annoyance, but I was just wondering if I could make my volume stay at 100% for every session anyways. Thx.

---

### Post by marc321 on 2007-06-20
Greetings!

First, set the volume to 100%, then open up a terminal and type the following:

```
sudo alsactl store
```

I'm in Gnome right now, so I can't remember the exact location of the terminal in KDE.  If you can't find it, press Alt-F2, type in *konsole*, and hit enter.

I take it you're running Kubuntu, or Ubuntu with KDE, since you posted here.  For any other distro, you'll probably have to log in as root and run *alsactl store*, since sudo isn't often set up like it is in (K)Ubuntu.

---

### Post by clk99 on 2007-06-20
thanks much

---

### Post by clk99 on 2007-06-20
Hmm, I may have thanked you too soon.  After a reboot my volume is still reverted to 10%.

---

### Post by marc321 on 2007-06-20
Well, hmm...  

Give this a shot in the terminal:

```

cd /var/lib/alsa
sudo mv asound.state asound.state.bak

```

Then run 

```

alsamixer

```

and set your volume to the desired levels. Finally, run

```

sudo alsactl store

```

I hope this works for you!

---

### Post by clk99 on 2007-06-20
Still no success.

I'm not sure how important it is, but maybe I should add that in Session Manager I have "On Login" set to "Start with empty session."

---

