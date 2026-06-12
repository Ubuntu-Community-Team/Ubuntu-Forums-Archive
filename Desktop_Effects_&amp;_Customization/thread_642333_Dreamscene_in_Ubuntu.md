---
title: "Dreamscene in Ubuntu"
date: 2007-12-16
forum: Desktop Effects &amp; Customization
---

### Post by LinuxIsInnovation on 2007-12-16
I have heard that we can set a video as wallpaper using mplayer (Which appears like Windows Dreamscene for Vista).. Anybody with knowledge on this topic please guide me how to do it..

---

### Post by Toet on 2007-12-16
It uses xwinwrap and mplayer.

Command line: xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet tv:// -tv driver=v4l:width=640:height=480: outfmt=i420

---

### Post by LinuxIsInnovation on 2007-12-16
Sorry but Im just a bit too new to ubuntu..
If you have time, please tell me stepwise.. Where do I get xwinwrap.. Its not there in Synaptics.

---

### Post by Toet on 2007-12-16
xwinwrap is available in a .deb somewhere on the internet.

install it using:

```
sudo dpkg -i xwinwrap_something.deb
```

have mplayer installed, and try the command I posted earlier.

---

### Post by LinuxIsInnovation on 2007-12-16
I'll do this and post the result.. thanx :)

---

### Post by Locutus_of_Borg on 2007-12-16
I've never been able to get xwinwrap to display anything but a blue screen when doing this

---

### Post by LinuxIsInnovation on 2007-12-17
Yes.. same here..
First, I stop nautilus.. That makes my desktop icons disappers
Then I set the wallpaper thru xwinwrap, but I get a blue screen there

---

### Post by Toet on 2007-12-17
Yep sorry, this is one where you get your webcam to be at the desktop.

The one with the video I can't find anymore. Sorry, I thought it was this one.

I'll have a harder look to see if I can find it again.

---

### Post by Toet on 2007-12-17
At least you have xwinwrap now... ;)

Try this:

[http://ubuntuforums.org/showthread.php?t=222193](http://ubuntuforums.org/showthread.php?t=222193)

---

### Post by LinuxIsInnovation on 2007-12-18
It says that I'll get a scripts option when I right click on vids.. But Im not gettin any scripts option.. :(

---

### Post by LinuxIsInnovation on 2007-12-21
Bump.

---

