---
title: "Low FPS and crazy sound in Doom 3"
date: 2006-07-30
forum: Gaming &amp; Leisure
---

### Post by Faytz on 2006-07-30
For some reason everytime i start Doom 3 the sound is horrible and even with all the settings low i get a poor fps.Tested in Windows and it worked fine.
Specs:
1.66 ghz intel core solo processor
1 gig of ram
128mb gfx card
80gb hard drive

---

### Post by Polygon on 2006-07-30
try adding

+set s_driver oss

after whatever the command is to start doom 3 in terminal, or paste it after it in the launcher command box.

---

### Post by Matrix101 on 2006-07-30
Try starting Doom3 with nice -n19 *doom3-executable*.That should fix the choppy sound plus the low fps.

BTW:What 3D-Card are you using?Nvidia or Ati?

---

### Post by Faytz on 2006-07-30
> **Polygon said:**
> try adding

+set s_driver oss

after whatever the command is to start doom 3 in terminal, or paste it after it in the launcher command box.
this worked but instead i get a graphical problem in the beginning i see black people standing(no racist remark intended)
And when i press ESC part of the screen is white

My gfx card is Intel i have updated driverts

---

### Post by Polygon on 2006-07-30
are your sure that your gfx card can actually HANDLE doom 3? I would think that unless that card uses an ati/nvidia chipset, it is probley not the best gfx card for gaming...

---

### Post by Faytz on 2006-07-30
Absolutely positive
minimum requirements for doom 3 is 64mb gfx card
i have 128mb

---

### Post by Matrix101 on 2006-07-31
Although 64 MB is the minimum, the Intel drivers have to support 3D-Accelaration under Linux.

---

### Post by sorcererx84 on 2006-07-31
You can't play Doom 3  under Linux with Intel video card. I have Intel GMA 900 (i915). Even in Windows I got around 20 fps with the latest drivers.

---

### Post by Faytz on 2006-07-31
thats the difference you have a GMA 900 i have a 945 chipset

---

### Post by Polygon on 2006-07-31
like someone said above, aer you sure you have 3d acceleration enabled for your video card?

---

### Post by Faytz on 2006-07-31
yes i do

---

