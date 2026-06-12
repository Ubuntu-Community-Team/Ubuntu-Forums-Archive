---
title: "HOW TO get sound on your Dell Insiron 1520 (Tutorial)"
date: 2007-12-05
forum: Dell  Ubuntu Support
---

### Post by painejake on 2007-12-05
Okay so im really new to Linux and Ubuntu, and i had real problems getting the sound to work at all on my notebook so here is a very simple way of getting the sound drivers for it. Im not sure whether this will work on other Dell Inspiron's.

just open terminal and copy and paste :

**sudo apt-get install linux-backports-modules-generic** 

and that's it. Very easy. Now just reboot and enjoy the sound!! :guitar:

Hope this stops people searching for days (as i did) and finding out the command was so simple.

Enjoy your new sound! :lolflag:

---

### Post by adityakiran on 2007-12-06
thnx man tis is great!!!!!!!!
it works!!!

---

### Post by moleculeman on 2007-12-07
Thank you very much. Now I can experience the full power of my tiny weak little notebook speakers :-)

---

### Post by alfredska on 2007-12-07
> **painejake said:**
> Okay so im really new to Linux and Ubuntu, and i had real problems getting the sound to work at all on my notebook so here is a very simple way of getting the sound drivers for it. Im not sure whether this will work on other Dell Inspiron's.

just open terminal and copy and paste :

**sudo apt-get install linux-backports-modules-generic** 

and that's it. Very easy. Now just reboot and enjoy the sound!! :guitar:

Hope this stops people searching for days (as i did) and finding out the command was so simple.

Enjoy your new sound! :lolflag:

This information, as well as other helpful 1520/Gutsy tips can be found on the "Installing Gutsy on Inspiron 1520" thread [here]("http://ubuntuforums.org/showthread.php?t=577469&highlight=1520").

---

### Post by mcauley on 2007-12-08
Worked perfecr on my 1520. Even the buttons on the front work.

Thanks,
Scott.

---

### Post by auspea on 2007-12-11
You Da Man!

Worked first time, after spending hours working on it.

Thanks
A

---

### Post by conehead77 on 2008-01-05
This worked flawless!

I spent quite some time with compiling new ALSA drivers and some other weird stuff.
After being without sound since Gutsy its just amazing how easy the solution was. Big Thanks from me!

And i dont have a 1520, only a simple desktop with a HDA-Intel soundcard  :KS

---

### Post by ssshahapure on 2008-01-13
> **painejake said:**
> Okay so im really new to Linux and Ubuntu, and i had real problems getting the sound to work at all on my notebook so here is a very simple way of getting the sound drivers for it. Im not sure whether this will work on other Dell Inspiron's.

just open terminal and copy and paste :

**sudo apt-get install linux-backports-modules-generic** 

and that's it. Very easy. Now just reboot and enjoy the sound!! :guitar:

Hope this stops people searching for days (as i did) and finding out the command was so simple.

Enjoy your new sound! :lolflag:

even I use Dell inspiron 1520 but could not connect to internet because even Conexant modem D330 model could not be detected in Ubuntu 7.10.I tried downloading above said package from packages.ubuntu.com using Windows but even its installation requires Internet connection.
Is there any other way to install above package?

---

### Post by painejake on 2008-01-29
No i don't think there is sorry you really need to be connected to the net to get really much out of Ubuntu. Especially in the setup :D
BTW When i put Ubuntu on my Dell Inspiron i had to connect through my Ethernet cable and then you get the broadcom Restricted drivers and after that you can connect via wireless.
Hope this helps :)

---

### Post by meshica7 on 2008-01-29
Man...I can't wait to see if this will work on my Dell Inspiron 1100 running Kubuntu 6.06!

---

### Post by airfreq on 2008-01-30
Hi i tried this on mine and it wont work unless im doin something wrong i am new to this so simple instructions please i really would like to have sound. i have set my 1520 up as a dual boot with vista home basic. which was pre installed but i would like to get to know ubuntu.

---

### Post by honzik.nemec@seznam.cz on 2008-04-03
Just works!! Thanks a bunch man :-)

---

### Post by DJRhubarb on 2008-04-06
Thanks man, this works just fine, I too had spent hours trying to find a solution for it but now everything is sweet. Thanks

---

