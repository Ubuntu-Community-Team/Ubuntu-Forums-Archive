---
title: "Quake3 + App's Menu = No Sound"
date: 2005-10-24
forum: Gaming &amp; Leisure
---

### Post by GIBson3 on 2005-10-24
:confused:  I'm sure it's my app entity that's the issue, but here it goes.

at a terminal issuing the following...
```

gib@edge$ /usr/local/bin/quake3

```

Gives me a fully working Quake 3 Arena.

I made an app entry in the games Menu that runs '/usr/local/bin/quake3' and quake 3 runs, but I'm missing sound, completely. 

I've tried the "Run in terminal" option with no luck, any idea's what may be causing this?

---

### Post by GIBson3 on 2005-10-24
ok a little more "research" today while I eat my Chili...

```
gib@edge:~$ /usr/local/bin/quake3
```
Gives me no sound...

```

gib@edge:~$cd /usr/local/bin
gib@edge:/usr/local/bin$./quake3

```
and sound works.

being that /usr/local/bin is in my PATH my next thought....

```

gib@edge:~$ quake3

```

again quake3 runs, but I get no sound....

I'm baffled:confused:

---

### Post by zachtib on 2005-10-24
well, you just saved me $20, i was about to buy a new sound card because i thought my current one didnt work with doom3.  the same thing you describe works to give me sound in doom 3.  if anyone has a better fix for this, id be interested to hear

---

### Post by kalin on 2005-10-24
A quick and dirty solution would be to create a script that changes the working directory first, and then starts quake3.

Then simply start the script in the corresponding Games menu entry.

---

### Post by zachtib on 2005-10-24
i tried that, no luck. if i run the script from my home directory, the game works fine (from a terminal type sh doom3.sh) put putting it in the gnome menu doesnt work.

keep in mind that myself and the OP are running two different games, but i think we are having the same problem


btw, GIBson3, what sound card do you have?

---

### Post by GIBson3 on 2005-10-24
[QUOTE=kalin]A quick and dirty solution would be to create a script that changes the working directory first, and then starts quake3.

Then simply start the script in the corresponding Games menu entry.[/QUOTE]

LOL I had considered this, However I've found a "cleaner" solution.

the issue seems to stem from the "Sound for Events" option under [[COLOR="Red"]system[/COLOR]]->[[COLOR="Red"]preferences[/COLOR]]->[[COLOR="Red"]sound[/COLOR]]  Once I turned that off it all of a sudden works, with no issues... only "down side" my Menu's don't make clicking noises, I'm going to HAVE to learn to live with out <scoff>  I tried switching to OSS/ALSA from the Default ESD neither worked.  I appears that a sound mixer is a little missing?

anyway Deathmatches durring lunch should be more enjoyable now.  :D:D:D

---

### Post by GIBson3 on 2005-10-24
[QUOTE=zachtib]i tried that, no luck. if i run the script from my home directory, the game works fine (from a terminal type sh doom3.sh) put putting it in the gnome menu doesnt work.

keep in mind that myself and the OP are running two different games, but i think we are having the same problem


btw, GIBson3, what sound card do you have?[/QUOTE]

Intel 82801BA-ICH2

What about yourself?

---

### Post by zachtib on 2005-10-24
The integrated sound on my ASUS A8N-SLI, its an nForce4 chipset.  A guy on another forum had a similar problem as us (no sound in quake3), he fixed it by buying a sound card based on the CMI8738 chipset, but as we can both get sound in some way, i think there should be a fix for this

---

### Post by GIBson3 on 2005-10-24
[QUOTE=zachtib]The integrated sound on my ASUS A8N-SLI, its an nForce4 chipset.  A guy on another forum had a similar problem as us (no sound in quake3), he fixed it by buying a sound card based on the CMI8738 chipset, but as we can both get sound in some way, i think there should be a fix for this[/QUOTE]


What's listed in...
[[COLOR="Red"]system[/COLOR]]->[[COLOR="Red"]preferences[/COLOR]]->[[COLOR="Red"]sound[/COLOR]]

as your device?

and I agree I don't see why our audio isn't able to mix,  Especailly since you are running a NF4... I could almost believe it off of a Intel 815 Mobo sound card.

I'm going to keep looking for information I'll post anything I find.  Who knows maybe I'll help someone else in the future.

---

### Post by zachtib on 2005-10-24
NVidia CK804

---

### Post by GIBson3 on 2005-10-24
According to the ALSA site, the nForce chipsets all use the Intel8X0 driver (as does my intel 815).  It appears that some configuration of the ALSA system is required to get this all working?  I'll look in to it more a bit later.

---

### Post by GIBson3 on 2005-10-25
Ok...

I've been poking around the ALSA website, and through a few links found

```
$cat /proc/asound/pcm
00-00: Intel ICH : Intel 82801BA-ICH2 : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : Intel 82801BA-ICH2 - MIC ADC : capture 1
$
```

So the Device is only capable of 1 playback and 1 Capture?  or is it 1 playback 2 capture. (I'm assuming it's 1 play back, one capture for Line in and another for the Mic)  Never the less there is no Hardware support for multiple channel playback. Which means you have to fall back to a software mixer. Fine and dandy, except Quake3 uses OSS and not ALSA... and thus the search continues.

anyone else able to post their [COLOR="Blue"]cat /proc/asound/pcm[/COLOR] if you are running ALSA?

---

### Post by Staesys on 2005-10-25
Does this work?

```
doom3 +set s_driver oss
```

---

### Post by GIBson3 on 2005-10-25
Won't for me D3 on a 1gig p3 is going to be suck...  Plus Q3A natively runs OSS =(

---

