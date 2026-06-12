---
title: "Optiplex internal speaker sound"
date: 2010-10-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by qakiudldu on 2010-10-18
Maybe it's just me, but I wanted to share how I fixed the problem of 'no sound from internal speaker' for my optiplex 960. 

I searched and many suggest running 'alsamixer' from the terminal and boost up the volume of 'mono' or 'internal speaker', which never worked for me. 

Instead, I installed 'gnome-alsamixer' from synaptics, which did the trick.

1. run the program from the terminal by typing 'gnome-alsamixer' (for some reason it never showed up from the application menu)
2. make sure the 'mute' is unchecked for 'mono'. 
3. now you have sound, although dinky, from the internal speaker. 

In the windows era, the internal speaker automatically switched on/off based on whether I had a headset in the jack, but I am not sure how to make that happen. 

Cheers,
Qaki

---

### Post by nosbor73 on 2010-10-26
hi qakiudldu

which version of unbuntu did you use. 
im looking to buy a new dell pc that will install unbuntu.

---

### Post by oldschoolgentoo on 2010-10-26
when i get to the office i have a 690, with 9.10 I had to reinstall this  box.  The first time i had no sound.  Afer the reinstall  i have sound from the headphone jacks.

I will check the system and find out what worked to get sound and post it.

---

### Post by nosbor73 on 2010-10-30
hi, im looking for a new dell. if you go to dell website the 690 is not there anymore.
so anyone who has bought a new recent dell, and installed unbuntu i would like to know which model and which version of unbuntu.

---

### Post by oldschoolgentoo on 2010-11-19
> **nosbor73 said:**
> hi, im looking for a new dell. if you go to dell website the 690 is not there anymore.
so anyone who has bought a new recent dell, and installed unbuntu i would like to know which model and which version of unbuntu.

Not a new dell  

2010 i686 GNU/Linux
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

 2.6.31-22-generic-pae

Dell Percision 690

[http://www.dell.com/us/en/gen/desktops/precn_690/pd.aspx?refid=precn_690&s=gen](http://www.dell.com/us/en/gen/desktops/precn_690/pd.aspx?refid=precn_690&s=gen)

video- quadro fx3500

---

### Post by dr_makhan on 2011-07-13
Thanks qakiudldu. This also solved my problem. I am using Dell Optiplex 330, Ubuntu 10.04.

---

