---
title: "Gnome sensors applet: alarm command line?"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Pjotr123 on 2006-08-18
Hi,

I installed lm-sensors and gnome sensors applet. Nifty! But now I want an alarm sound and/or popup, when the temperature becomes too high. Which command line can I use in the Preferences section of gnome sensors applet?

Thanks in advance, Pjotr.

---

### Post by reclusivemonkey on 2006-08-18
> **Pjotr123 said:**
> Hi,

I installed lm-sensors and gnome sensors applet. Nifty! But now I want an alarm sound and/or popup, when the temperature becomes too high. Which command line can I use in the Preferences section of gnome sensors applet?

Thanks in advance, Pjotr.

You can use the command line alsa player to play a wav/mp3;

```

aplay *filename*

```

You can use zenity or notify to display a pop up menu. I am at work at the moment, but you can search the forums for more info on this. I'll post back when I get home if you haven't got an answer by then. HTH

---

### Post by Pjotr123 on 2006-08-18
> **reclusivemonkey said:**
> You can use the command line alsa player to play a wav/mp3;

```

aplay *filename*

```

You can use zenity or notify to display a pop up menu. I am at work at the moment, but you can search the forums for more info on this. I'll post back when I get home if you haven't got an answer by then. HTH

Alsa player works fine! Thanks a lot. 

Now, can I combine this sound warning with a popup message? I don't know which command line to use in order to activate "notify".

Pjotr.

---

### Post by reclusivemonkey on 2006-08-18
> **Pjotr123 said:**
> Alsa player works fine! Thanks a lot. 

Now, can I combine this sound warning with a popup message? I don't know which command line to use in order to activate "notify".


You can use "notify-send" or zenity. You should be able to do something like;

```

notify-send WARNING "CPU fan speed too low" & aplay /usr/share/sounds/warning.wav

```

or

```

zenity --warning --text "CPU temp too high" & aplay /usr/share/sounds/warning.wav

```

man zenity and notify-send for more options. :)

---

### Post by Pjotr123 on 2006-08-18
Thanks again! The trick with zenity works like a spell.

One last question: is it also possible to make the computer power off automatically when the temperatures are too high? If so, do you know which command line I can use?

Pjotr.

---

### Post by reclusivemonkey on 2006-08-18
> **Pjotr123 said:**
> Thanks again! The trick with zenity works like a spell.

One last question: is it also possible to make the computer power off automatically when the temperatures are too high? If so, do you know which command line I can use?


You should have this feature in BIOS; every modern motherboard will shut down if it gets too hot. If you want to do this automatically, you will need to look at /sbin/shutdown. As always, the "man" is your friend.

---

### Post by kevin_williams on 2006-11-09
sorry about asking a question on your thread

i'm using the sensors-applet to start my fan when my computer reach the high value (using i8k)
however, i was wondering how i could stop the fan when the temp reach the low value

my alarm command is simply "i8kctl fan 2 2"
TIA

---

