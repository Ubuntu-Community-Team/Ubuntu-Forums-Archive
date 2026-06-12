---
title: "dell d620 noise on shutdown"
date: 2009-11-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Gatorade on 2009-11-12
I've just installed Ubuntu 9.04 on a dell d620 laptop. when I shut it down , however, it squawks a couple of loud beep before turning off.

I've tried shutting the speakers off, but it still does it.

anyone know why its doing this?

now that I think about it , I think my other pc does the same thing. but it doesn't beep at full volume so I just never really gave it much thought.

so, I guess my question should be 'how do I turn down the volume?' on shut down instead.

---

### Post by Zoot7 on 2009-11-12
If you want to permanently disable it do this:
```
gksu gedit /etc/modprobe.d/blacklist
```

And add this line to the end, save and close.
```
blacklist pcspkr
```
The next time you reboot, it should be disabled. Or if don't want to wait to a reboot do this:
```
sudo modprobe -r pcspkr
```

Failing that, install the Gnome Alsa Mixer:
```
sudo apt-get install gnome-alsamixer
```

Then open that, and there should be an option for the "PC Beep", you can just mute it from there.

---

### Post by Gatorade on 2009-11-13
thanks , I already got it .

but the mute suggestion may come in handy one day.

---

### Post by Zoot7 on 2009-11-13
Glad to hear you're sorted, but would you mind posting what you did? It might help others with the same issue in the future. ;)

---

### Post by tommynz1975 on 2009-11-13
Zootr 

I had the same issue, just followed your 1st 3 steps

I have a dell dimension 2400. I had not experienced this under 6.06.

I know this is marked solved, but in the spirit of learning can I ask why the beeps?

It was just by chance I looked and noticed this thread.

one issue is that after passing the 3rd command  you suggested is the system response was that in later versions this wont be available with out a conf file

---

### Post by Zoot7 on 2009-11-13
I think the main reason for the beep is system alerts, although IMO it's just a rather obnoxious annoyance.

Re the 3rd command: What that does is remove the module 'pcspkr' (the one that causes the beeps) from the kernel while you're running the OS at the time.

---

### Post by Gatorade on 2009-11-13
> **Zoot7 said:**
> Glad to hear you're sorted, but would you mind posting what you did? It might help others with the same issue in the future. ;)

I just did what you said, the first two commands did it.

here's a link to a tutorial which another poster recommended.
[http://ubuntuguide.net/disable-the-annoying-beep-when-you-shutdown]("http://ubuntuguide.net/disable-the-annoying-beep-when-you-shutdown")

---

### Post by Zoot7 on 2009-11-14
> **Gatorade said:**
> I just did what you said, the first two commands did it.

here's a link to a tutorial which another poster recommended.
[http://ubuntuguide.net/disable-the-annoying-beep-when-you-shutdown]("http://ubuntuguide.net/disable-the-annoying-beep-when-you-shutdown")
Ah ok. :)

---

