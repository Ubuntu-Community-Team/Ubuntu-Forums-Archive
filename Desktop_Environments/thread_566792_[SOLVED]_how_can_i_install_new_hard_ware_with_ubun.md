---
title: "[SOLVED] how can i install new hard ware with ubuntu plez help"
date: 2007-10-03
forum: Desktop Environments
---

### Post by tropcky on 2007-10-03
i just got a creative sound card   so how can i install in in ubuntu  i did it with win xp by  add new hardware  but how can i do it with ubuntu     
thank u all

---

### Post by peabody on 2007-10-03
You might try opening a terminal window and typing this in:

sudo dpkg-reconfigure alsa-base

Hopefully it'll see your new soundcard in there.  If not, post here again.

---

### Post by tropcky on 2007-10-03
it didnt work man

---

### Post by peabody on 2007-10-03
Can you give me a little more information than "it didn't work man?".  I'm left to guess what the problem could be.  What happened when you tried it?

---

### Post by tropcky on 2007-10-03
just nothing at all 

tropcky@tropcky-Linux:~$ sudo dpkg-reconfigure alsa-base
tropcky@tropcky-Linux:~$

---

### Post by peabody on 2007-10-03
Sorry about that, try

sudo alsaconf

That should be what we're looking for.

---

### Post by tropcky on 2007-10-03
tropcky@tropcky-Linux:~$ sudo alsaconf
Password:
sudo: alsaconf: command not found

---

### Post by peabody on 2007-10-03
Yikes!  Okay, this is news to me.  alsaconf apparently is not present in the ubuntu distro.  I have it because I had to do a manual install of alsa to get my particular soundcard working.  I'm going to have to do some research.  This is really weird, why would Ubuntu remove that?

---

### Post by tropcky on 2007-10-03
i dont know.  they remove  it and i lose it

---

### Post by tropcky on 2007-10-04
any one

---

### Post by SpiritIsReality on 2007-10-04
howdy
Ya, I'd like to know why no alsaconf.
OK. I don't know exactly what to do if it doesn't just work, except with look at sound card and read the chip name, or google the name model and get chip name; then go to alsa [www.alsa-project.org](www.alsa-project.org) and find the driver for the chip, then add that to the /etc/modules file (and then run alsaconf if runnin' debian, but in ubuntu it is not necessary.?) soooo..
could try this if sound card not recognized and no sound: ? hopefully others who know better than I will post.[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)
[http://www.google.ca/search?as_q=creative+sound+card&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&as_ft=i&as_filetype=&as_qdr=m6&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images](http://www.google.ca/search?as_q=creative+sound+card&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&as_ft=i&as_filetype=&as_qdr=m6&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images)
[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs)
buds

---

### Post by tropcky on 2007-10-04
thank u so much

---

### Post by SpiritIsReality on 2007-10-04
howdy
What card do you have? What did you have to do to get it working?
Did you find a driver at alsa and add it to /etc/modules or ?
for a crystal semiconductor cs4237B-KQ...I had to add snd-cs4236 I think to /etc/modules.

buds

---

### Post by tropcky on 2007-10-04
i  no i just turned the pc off cut off the power remove the card and put it in anther port 
and when i start the pc agen  it  worked 
just by it self

---

### Post by SpiritIsReality on 2007-10-04
howdy
Good News.!
all the best
buds

edit : install hardware, searched [http://www.google.ca/search?hl=en&q=site%3Aubuntu.com+%22install+hardware%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntu.com+%22install+hardware%22&btnG=Google+Search&meta=)
see heading:Connecting And Configuring Hardware here [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

---

