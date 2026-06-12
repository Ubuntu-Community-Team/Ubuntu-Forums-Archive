---
title: "help  with sound dont work"
date: 2007-10-01
forum: Desktop Environments
---

### Post by tropcky on 2007-10-01
i had to chang my motherboard today and i got a gigabyte one   and when i run my pc 
ther is no sound at all no music no play back nothing and when i trayed to open the  restricted drivers manager  it told me :    Your hardware does not need any restricted drivers.
 plez help

---

### Post by tropcky on 2007-10-01
guys plez help   the audio Shep is :Realtek ALC650E/655 Audio AC'97 CODEC

---

### Post by maryjanua on 2007-10-01
i had the same problem with a realtek alc888
i had to compile alsa
i'll post the thread :)

---

### Post by tropcky on 2007-10-01
ya man plez  thank u so much

---

### Post by maryjanua on 2007-10-01
here u go 
[http://ubuntuforums.org/showpost.php?p=3379876&postcount=66](http://ubuntuforums.org/showpost.php?p=3379876&postcount=66)

[http://ubuntuforums.org/showpost.php?p=3390143&postcount=106](http://ubuntuforums.org/showpost.php?p=3390143&postcount=106)

hope this helps
youll have to get the drivers for your own card from the manufacturers and replace the code i'd imagine.
:):)

---

### Post by tropcky on 2007-10-01
thank u so much bro

---

### Post by tropcky on 2007-10-01
it didnt work   
 plez help

---

### Post by mali2297 on 2007-10-03
> **tropcky said:**
> it didnt work   
 plez help

Did you manage to compile the driver alright?
...or did you get errors when following the instructions?

The original Howto is here:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

If you want more help, run these commands in the terminal and post the output:
```

uname -a
aplay -l
lspci -v | grep -A 5 Audio

```

---

### Post by jameson737 on 2007-10-06
It is very wierd that ubuntu 7.04 has a mysterious problem among the PC. No sound tends to happen frequently whener user boot from OS. Then user need to restart the whole PC to get the sound again. It happens to both new and old PC, Whatever sound card you have. 

It there any way to make this thing never happen again ?

Thanks in advance

---

