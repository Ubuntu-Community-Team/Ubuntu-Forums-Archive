---
title: "DVD playback on ubuntu 8.10 pain in the butt"
date: 2009-02-16
forum: General Help
---

### Post by nboy56 on 2009-02-16
this is my issue i used to have win xp then i switched to ubuntu 8.10. at first i got dvds to play with totem by installing a package like libcss2 or something like that but although it technically was playing there was no sound and you would watch the elapsed time go up but the screen was still black it was beyond choppy beyond even unwatchable it was better not even to have "DVD playback" so at first I thought it was  totem so I switched to VLC (which worked perfectly even in fullscreen on windows xp) but it had the same issues so is there anything i need to download to fix this like more packages??? plz help me with this

---

### Post by handy on 2009-02-17
Patiently have a look at this how-to, it will solve your problems, & it won't take you very long:

*_[http://ubuntuforums.org/showthread.php?t=766683&highlight=howto+DVD+playback](http://ubuntuforums.org/showthread.php?t=766683&highlight=howto+DVD+playback)_*

---

### Post by nboy56 on 2009-02-17
thanks but it said 32 bit ubuntu or 64 bit ubuntu wat does that mean???

---

### Post by taurus on 2009-02-17
It means either you are running x86 (32bit) or x86_64 (64bit).

Applications -> Accessories -> Terminal
```
uname -m
```

---

### Post by nboy56 on 2009-02-17
thanks ill try all this stuff out hopefully it works

---

### Post by nboy56 on 2009-02-27
Ok well there is no sound or video but the vlc claims its playing by the time elapsed shown but if I turn down the speed to .50X then it plays but obviously super slow I still need help it all worke perfectly on Windows xp bfore so yah

---

### Post by mb_webguy on 2009-02-27
That sounds like it might be a video driver issue, and not necessarily with DVD playback.  Do you have any problems playing media files?

---

### Post by nboy56 on 2009-03-02
yah how do I fix that driver issue though??? although the other day i put in the original dukes of hazzard and it played the menu fine but not the actual movie

---

### Post by nboy56 on 2009-03-03
hey did everyone forget me hello! i still need an answer

---

### Post by nboy56 on 2009-03-04
hello anyone there i could use some help here

---

### Post by taurus on 2009-03-04
Did you install libdvdcss2 from Medibuntu?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by mempman on 2009-03-04
Remove everything that you installed.
Just get VLC player with all its dependencies.  

[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

---

### Post by anjilslaire on 2009-03-04
rudeness won't get you far here.

try
```

sudo apt-get install ubuntu-restricted-extras

```
then try your movie in vlc or totem.

---

### Post by nboy56 on 2009-03-05
> **taurus said:**
> Did you install libdvdcss2 from Medibuntu?

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) 

Yes I did 

And Mempman how do I remove all of it and are you sure that will work?

Srry anjislare I wasnt trying to be rude but everyone did sorta leave me hangin there for  about 3 days so I apoligize

---

### Post by nboy56 on 2009-03-06
also is there any drivers i should download and how becasue i dont think that i have any hardware drivers on my computer

---

### Post by entr3p on 2009-03-06
Type these commands in the Terminal.

**sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list**
**wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update**
**sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 vlc**

I'm assuming your running Intrepid.

---

### Post by nboy56 on 2009-03-06
by intrepid you mean 8.10 ubuntu it said intrepid ibex on the disk and ill try that out sometime today thank you

---

### Post by entr3p on 2009-03-06
> **nboy56 said:**
> by intrepid you mean 8.10 ubuntu it said intrepid ibex on the disk and ill try that out sometime today thank you

Yup. Basically the latest version of Ubuntu out right now.

---

