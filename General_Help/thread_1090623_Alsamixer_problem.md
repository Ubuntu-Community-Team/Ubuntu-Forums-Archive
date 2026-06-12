---
title: "Alsamixer problem"
date: 2009-03-08
forum: General Help
---

### Post by Primi on 2009-03-08
I can't get my mic working so I wanted to check if it is muted. When i type alsamixer -command, there is only "master" bar. If I push F4 I can see "capture" bar. I had sound problem once before and I had to type some command before I could see all bars like in this picture [http://linux.fi/images/thumb/8/86/Alsamixer.png/800px-Alsamixer.png](http://linux.fi/images/thumb/8/86/Alsamixer.png/800px-Alsamixer.png)

Any idea what should I do or what was the command?

---

### Post by jocko on 2009-03-08
To access alsa instead of pulseaudio:
```
alsamixer -Dhw
```

---

### Post by Primi on 2009-03-08
> **jocko said:**
> To access alsa instead of pulseaudio:
```
alsamixer -Dhw
```

Does not help. There is only IEC958 bar.

Other ideas?

---

### Post by unutbu on 2009-03-08
Which version of Ubuntu are you using? 

Have you tried gnome-volume-control? You can launch the application by either typing "gnome-volume-control" at the terminal, or by adding the "Volume Control" applet to the gnome panel, right-clicking on the applet and selecting "Open Volume Control".

---

### Post by Primi on 2009-03-08
> **unutbu said:**
> Which version of Ubuntu are you using? 

Have you tried gnome-volume-control? You can launch the application by either typing "gnome-volume-control" at the terminal, or by adding the "Volume Control" applet to the gnome panel, right-clicking on the applet and selecting "Open Volume Control".

Thanks for the tip, didn't know that. Now mic is working... Well, not in TeamSpeak, but working on it.

---

