---
title: "Beryl and Videos"
date: 2007-05-26
forum: Desktop Effects &amp; Customization
---

### Post by tbob18 on 2007-05-26
I am using UbuntuStudio and am having a problem while running Beryl window manager and videos. With Beryl on I get tearing on the video I am playing, but when I go back to Metacity window manager everything works fine.
I have tried mplayer, VLC, totem, and SMplayer. I even get tearing with online videos from Youtube and Google. 

I have tried setting the video output to "no xv" but it just made it worse. I have also tried changing all of the setting in the "advanced beryl option" where you can select the renderer and what not.

I have a HP Pavilion zv5405us and the specs are:
Athlon 64 3200+
Geforce4 mx440 Go
Nforce 3 chipset

That is all that should really matter.

Just wondering if anyone knows if there is a fix for this. :D

Thanks.

---

### Post by tbob18 on 2007-05-27
Bump... Anyone?

---

### Post by Cresho on 2007-05-27
hmmm...lets see, we both almost have the same specifications.

here are a few settings i have enabled to get this to work.

Going into the Beryl settings manager->General options->Advanced, I ticked the "unredirect fullscreen windows" and "enable workarounds for certain wine legacy games" now my games play just fine. In addition, I also used the beryl manager->advanced rendering options->rendering options->and checked force aigxl. Now this combo made my setup run very nice. one last thing, i noticed I had problems with some-things so I clicked on disable gl under beryl manager->advanced rendering options for better performance.

with these settings, I am running HD content just fine.

---

### Post by tbob18 on 2007-05-28
> **Cresho said:**
> hmmm...lets see, we both almost have the same specifications.

here are a few settings i have enabled to get this to work.

Going into the Beryl settings manager->General options->Advanced, I ticked the "unredirect fullscreen windows" and "enable workarounds for certain wine legacy games" now my games play just fine. In addition, I also used the beryl manager->advanced rendering options->rendering options->and checked force aigxl. Now this combo made my setup run very nice. one last thing, i noticed I had problems with some-things so I clicked on disable gl under beryl manager->advanced rendering options for better performance.

with these settings, I am running HD content just fine.

Hmm, that did not seem to do much but slow it down even more.. Are you using an ATI card?

---

### Post by tbob18 on 2007-05-31
Still haven't found a fix, been playing around with it on and off for the last few days. Anyone else have some ideas?

---

### Post by TyPhoon101 on 2007-06-18
> **Cresho said:**
> hmmm...lets see, we both almost have the same specifications.

here are a few settings i have enabled to get this to work.

Going into the Beryl settings manager->General options->Advanced, I ticked the "unredirect fullscreen windows" and "enable workarounds for certain wine legacy games" now my games play just fine. In addition, I also used the beryl manager->advanced rendering options->rendering options->and checked force aigxl. Now this combo made my setup run very nice. one last thing, i noticed I had problems with some-things so I clicked on disable gl under beryl manager->advanced rendering options for better performance.

with these settings, I am running HD content just fine.

i also had tearing in the full screen video when running some mkv file in smplayer. i am using beryl manager. your suggestion seems to have fixed the problem.:D

---

