---
title: "[SOLVED] Sound not working [Hardy Heron 8.04]"
date: 2008-12-05
forum: General Help
---

### Post by Zyferian on 2008-12-05
Hey, guys... I'm relatively new to the Ubuntu community. I keep dabbling with it, getting fed up, and then leaving again... but this time I really do want to make a valiant effort at using it as my main system. :o

Anyway, recently upgraded the new install to an 8.04 Hardy Heron, my first of this particular release. And... I have no sound. I'm not sure why or anything like that but will be willing to provide any outputs to any commands that are so desired. It's a Dell Desktop, I believe Dimension class.

Thanks!

---

### Post by Zorael on 2008-12-05
First off, make sure your channels aren't muted.
```
$ alsamixer
```
The green [COLOR="Lime"]00[/COLOR] labels mark them as active, while MM means muted.


edit: First-and-a-half, try this in a terminal.
```
$ speaker-test -c2 -twav
```


Second, you say you upgraded? Have you tried it off a live cd/pendrive? There's been some significant changes whatwith PulseAudio having taken a central role. Anyway, try a live environment and see if it works there.


Third, if you have an Intel HDA sound chipset, you may need to pass a model identifier to the actual driver.
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: [COLOR="DeepSkyBlue"]**Intel [HDA Intel]**[/COLOR], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```
If it is indeed an Intel HDA, go read [http://ubuntuforums.org/showpost.php?p=5017453](http://ubuntuforums.org/showpost.php?p=5017453).

---

### Post by Zyferian on 2008-12-05
Okay, thank you so much, that was awesome. Soo... I found out that I did have an Intel HDA chipset (yay me) and fixed that part. Now, I have sound... but it's very faint. I have to turn my speakers all the way to maximum, along with all the sound options that I have on my volume control, to be able to hear it. Is that normal?

---

### Post by Happypants on 2008-12-05
If your sounds still low then you might try running:

```
 pavucontrol

```

and turning it up in there if you haven't already.

---

### Post by Zorael on 2008-12-05
Check your graphical volume mixer. If you're running GNOME (Ubuntu), hit Alt+F2 and run **gnome-volume-control**. If KDE, **kmix**. There are likely more than one slider (channel) that directly controls sound output, so make sure they're all way up there and try again.

For instance, I have **Master**, **Headphone**, **Front** *AND* **PCM**. Those four are all multiplicative, so I need to have all of them at decent levels to get any sound. (Ergo, if I have three of them at max and one at 0, I'll get 0 sound. Perhaps you have some similar setup.)

---

### Post by Zyferian on 2008-12-05
Okay, I actually think the problem is in my speakers this time. I knew they were a bit faulty anyway... but I kicked them a couple of times to see if they would work better and they didn't, so figured it was an Ubuntu problem (I should replace them... but they've been so good to me for so long...)

Anyway, looks like problem is solved... it's my crummy speakers. Thanks to Zorael for pointing out the  HDA Intel fix!

---

### Post by Zorael on 2008-12-05
Not at all. ;3

Mark thread as solved under Thread Tools, please. (edit: merely editing the title doesn't work once you've gotten replies to the thread, as far as I understand things.)

---

