---
title: "General slowness of the GUI"
date: 2009-10-24
forum: Desktop Environments
---

### Post by KONEY on 2009-10-24
HEllo everybody!

I'm usigng UBUNTU since a few months now after using XP for years (and still using it @ work) and I find its GUI quite slow compared to the XP one. My computer is a dual core with all the right drivers, in fact it has good performances, but lot of everyday task have a slight  (maybe 400ms) delay, like resizing a window, fullscreening it, unminimizing it...all this compared to a super-smooth compiz 3D cube desktop that makes the delays look strange. All this tasks in XP are real time-super-fast responding... 

Is there something wrong on my setup or is it normal? and if it's normal, could it be fixed in the future?

Many thanx!

---

### Post by arcull on 2009-10-24
Hi, do you have drivers for you graphic card installed? Open konsole and type```
glxgears
```, how many fps do you get, If it is around 200 or less, you don't have the right drivers installed. Some other suggestion: open konsole and type top, to see processes which consume most of your capacities.

---

### Post by KONEY on 2009-10-24
Thanx for your reply!

```
koney@BEAST2-UBUNTU:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately 1/1287142 the monitor refresh rate.
12788 frames in 5.0 seconds = 2557.498 FPS
12088 frames in 5.0 seconds = 2417.572 FPS
12372 frames in 5.0 seconds = 2474.335 FPS
13222 frames in 5.0 seconds = 2644.311 FPS
13164 frames in 5.0 seconds = 2631.438 FPS
14832 frames in 5.0 seconds = 2966.263 FPS
13888 frames in 5.0 seconds = 2777.588 FPS
13853 frames in 5.0 seconds = 2770.484 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 46 requests (45 known processed) with 0 events remaining.

```

Seems like the performances are goot!

Top shows me 4% cpu used... the computer goes well only the GUI don't respond as I'm used to! :(

---

### Post by arcull on 2009-10-24
I don't know for gnome, but if you use kde, try changing window manager, if you use compiz try changing it to kwin, which provides similar effects, Configure Desktop > Default Applications > Window Manager and see if it gets any better

---

### Post by entikryst on 2009-10-24
Your could try downloading the Fluxbox or Blackbox window manager or try the xfce desktop environment. All can be downloaded with synaptic and enabled at the login window.

---

### Post by zlatkart on 2009-10-24
Try a different theme. Maybe Mist as a test. However the GUI in Ubuntu is slower than XP.

---

### Post by KONEY on 2009-10-24
ah so it IS slower! Hope this get improved one day!


Anyway remover Compiz, not much improvment...

---

### Post by TheStroj on 2009-10-24
> **KONEY said:**
> ah so it IS slower! Hope this get improved one day!


Anyway remover Compiz, not much improvment...

Not really true. It is really fast by me and I don't have some supercomputer. I have tons of compiz effects enabled and I have screenlets running and it works as good as new. Even if I get my CPU running at 95% and my RAM to 95% it still works fast (opening windows is normal, opening new programs too).

Don't know why it runs slow by you, but you could try setting effects to 'None' in System-Preferences-Appearance-'Effects' tab.

---

### Post by KONEY on 2009-10-24
I dont know...for example this firefox windows iconifies very fast but it takes nearly one second to maximize again....:confused::confused:

---

### Post by diesch on 2009-10-24
What graphic card do you have? Ubuntu 9.06 has performance problems with most Intel graphic cards.

---

### Post by KONEY on 2009-10-24
I think everything in this computer is asus.

Removed compiz and now multiple desktops don't work anymore :((

---

### Post by KONEY on 2009-10-24
UPDATE: I didnt remove compiz! It was still active, now I completely removed it and there's a good improvment! (also problems discussed in another topic with video playback are gone)

So that _was_ the main problem! thanx all guys!

Now I just need another better desktop manager :))

---

### Post by Barriehie on 2009-10-24
> **KONEY said:**
> UPDATE: I didnt remove compiz! It was still active, now I completely removed it and there's a good improvment! (also problems discussed in another topic with video playback are gone)

So that _was_ the main problem! thanx all guys!

Now I just need another better desktop manager :))

I don't care/need any flashy desktop effects so for the sake of speed I use metacity.  It's like cheerios compared to fruit loops and I've compiled it for my machine.  It's quite quick.  To use metacity instead of compiz type this in the terminal:
```

metacity --replace

```

Barrie

---

### Post by KONEY on 2009-10-24
I tried this but something went wrong and I lost all my windows gadgets...so I removed it and something went even wronger, now I get a X-win style desktop from nineties...HELP!

---

### Post by Barriehie on 2009-10-24
> **KONEY said:**
> I tried this but something went wrong and I lost all my windows gadgets...so I removed it and something went even wronger, now I get a X-win style desktop from nineties...HELP!

Try System > Preferences > Appearance and select normal.

Barrie

---

### Post by KONEY on 2009-10-25
Ok I got it. I unistalled also metacity common which have lot of modules, put it back and everything is fine. I had a heartattack :)

---

### Post by Barriehie on 2009-10-25
> **KONEY said:**
> Ok I got it. I unistalled also metacity common which have lot of modules, put it back and everything is fine. I had a heartattack :)

So is it faster???

Barrie

---

### Post by KONEY on 2009-10-25
Totally!

---

