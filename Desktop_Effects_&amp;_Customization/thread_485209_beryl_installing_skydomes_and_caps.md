---
title: "beryl installing skydomes and caps"
date: 2007-06-26
forum: Desktop Effects &amp; Customization
---

### Post by halesquad on 2007-06-26
sorry to post here but i don't know where else to get such a quick response.

i am new to beryl and ubuntu and i really am enjoying messing with all the settings but i just can't install anything on the top of the cube or in the background. 

Please point me in the right direction for a real beginner

Thanks 

Stephen

---

### Post by sailor2001 on 2007-06-26
in cube settings/caps/ you can browse for the jpeg you want.....also you have to set your opaque down a bit.

---

### Post by Vajra Vrtti on 2007-06-26
In *System Tools -> Beryl Manager*, select *Desktop -> Desktop Cube*.
Set the top image in the *Caps* tab and the background in the *Skydome* tab.

---

### Post by halesquad on 2007-06-26
can you give me an example image to try as the ones that i am using are not working, i got them from here.

[http://beryl-look.org/index.php?pageNum_rstItemsByCatID=4&totalRows_rstItemsByCatID=58](http://beryl-look.org/index.php?pageNum_rstItemsByCatID=4&totalRows_rstItemsByCatID=58)

what am i doing wrong

---

### Post by quinnten83 on 2007-06-26
It sorta depends, 
I running with an ati radeon mobility 7500 and it can't handle everything. I noticed that only skyport images in 1024x1024 get displayed. I also know that some images can be used for the caps, but i haven't figured out which dimensions it can handle.
On my other pc, the images seem to work just fine when i tried the live CD.

---

### Post by Vajra Vrtti on 2007-06-26
The images I use for cube caps and skydome are ordinary wallpapers. They are both 1600x1200 jpeg files.
My video card is nVidia 6200 and I am using the Beryl version found in Feisty repositories.

---

### Post by d_xtremw on 2007-06-26
from what i know most images work for the caps but for the skydomes it must:

1) be in .png format
2) have dimensions of some form of power of 2 
      ie. any combination of these  128, 256, 512, 1024, 2048 , 4096  x  128, 256, 512, 1024, 2048, 4096

     but you need to check how much your graphics card can support. theres a thread on it here somewhere

---

### Post by Clay_Banger on 2007-06-26
> **d_xtremw said:**
> from what i know most images work for the caps but for the skydomes it must:

1) be in .png format
2) have dimensions of some form of power of 2 
      ie. any combination of these  128, 256, 512, 1024, 2048 , 4096  x  128, 256, 512, 1024, 2048, 4096

     but you need to check how much your graphics card can support. theres a thread on it here somewhere
i believe what you are after is this command:
```
xvinfo | grep max
```
type that into the terminal and the largest number it spits out is the largest you can go in the power of 2 combinations. so mine is:
```
~$ xvinfo | grep max
    maximum XvImage size: 1920 x 1088
    maximum XvImage size: 2048 x 2048

```
so i can only using images that dont go above 2048 on any side.

---

### Post by dustigroove on 2007-06-26
[FONT=Arial][SIZE=2][COLOR=Black]The aforementioned thread...
[http://ubuntuforums.org/showthread.php?t=301414&highlight=beryl+xgl+skydome+ati](http://ubuntuforums.org/showthread.php?t=301414&highlight=beryl+xgl+skydome+ati)

Cheers

[/COLOR][/SIZE][/FONT]

---

