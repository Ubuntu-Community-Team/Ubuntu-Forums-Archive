---
title: "Dell Mini 9 sound issues with 8.10"
date: 2008-10-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by techxplorer on 2008-10-28
I took delivery of my Dell Mini 9 last week and because I'm in Australia I had to get the WinXP version. 

I've since installed Intrepid Ibex (8.10) on it and everything is working really well except for the sound. 

If I turn up the sound using the mixer enough to hear anything I also get a lot of static / white noise. 

To get any sound at all I added the following line to the end of my /etc/modprobe.d/alsa-base file

```
options snd-hda-intl index=0 model=dell
```

Does anyone have any ideas on how can I fix this problem? :confused:

---

### Post by schmindy on 2008-10-28
Same with my acer aspire 4720z. I expect it to be fixed in the next version of ubuntu. They usually do. Also as this is an extremely popular netbook it is likely that if it is a big issue the community will fix it. 
Sorry I could not help more,
Schmindy

---

### Post by techxplorer on 2008-10-29
Its embarrassing to admit, but I think I've resolved my issue. 

Essentially I just had the Speaker and Master volume settings too high. By turning both down a bit, the Speaker more than the master, the static / white noise went away and my music was at an appropriate level to listen to. 

I guess this was just a case of over analysing the problem. :oops:

---

### Post by rht22696 on 2008-11-24
hi techexplore, can you tell me step by step how to get sound working
i can`t even get sound to work pls
and thanks 

i new with linx and command lines when i try i get a permisson denied
thanks again

---

### Post by ytsejam1138 on 2008-11-24
See this post:

[http://ubuntuforums.org/showpost.php?p=6178990&postcount=3](http://ubuntuforums.org/showpost.php?p=6178990&postcount=3)

---

### Post by rht22696 on 2008-11-24
thanks i will give it go tonight 
and keep you posted thanks alot

---

### Post by rht22696 on 2008-11-25
it worked thanks alot
 

problem solved

---

### Post by zorozadeh on 2009-02-16
I have purchased a 8.04 version of mini9 and I had the white noise on the audio output.It is not 8.10 problem,only.

---

### Post by pjamin on 2009-07-22
I have just purchased a Dell Mini 9 XP version. It also had the white noise problem that you have experienced. I fixed this by opening the master volume control properties and adding `pc beep` to the mixer and muting this channel. The white noise dissapears. I hope the problem doesn`t reappear when I install Ubuntu.

---

### Post by sbolt on 2011-04-11
I have a dell mini 9 and the speaker and headphone sound isn't working. I tried adding and muting "PC Beep" but that didn't work. The sound was fine until I downloaded "Audacity" - a recording program. I attempted to turn up the microphone in this program and now I have no sound to my lap top! Can anyone help?

---

### Post by mörgæs on 2011-04-13
Hi, welcome to the fora.

Your question does not seem to be specific to Dell. I guess best is to search here:
[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

---

