---
title: "Anyone using PCSX2 ??? on linux plz help me"
date: 2007-09-17
forum: Gaming &amp; Leisure
---

### Post by @vijay@ on 2007-09-17
IS there anyone playing ps2 games on linux using PCSX2 ?? .......... are the games playable ??
i recently installed PCSX2 0.9.3 on my ubuntu ....... but when i tried to start a game i get error like GS errror ; i believe its because mine is Intel graphics card

ACtually Intel 950 has to support Pixel shaders 2........... but i think it wont in linux (correct me if im wrong)

is there a way i can get the GSDX9 graphic plugin for linux ...... im unable to find but in windows version its thr
------------------------------------------------------------------
[B][U]MY SYSTEM SPECS ARE :
Intel core2duo 2.13 processor
inbuilt intel 950 GMA

are these enough to run PCSX2 and games ???? if not Which graphics card should i buy ????? any suggestions plzzzzzzzz.......
i really miss games on my linux system[/U][/B]

---

### Post by process91 on 2007-10-08
I'm pretty sure that error is always in relation to the cg toolkit. Just install the cg toolkit and see what happens.

In feisty and below you'll need to download the RPM for your architecture here, then use alien to convert it to deb and install it using dpkg.

In gutsy you can install it from the multiverse repo.

Code:

sudo apt-get install nvidia-cg-toolkit

I know you don't have nvidia, but try it out.

---

### Post by Ripfox on 2007-10-09
This is the same advice I got and it doesn't work, dudes. It is our Intel graphics...

---

### Post by Sockerdrickan on 2007-10-09
I get 40-60 fps in RE4

---

