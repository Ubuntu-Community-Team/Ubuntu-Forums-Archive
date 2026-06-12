---
title: "SkyDome Isn't working."
date: 2007-07-04
forum: Desktop Effects &amp; Customization
---

### Post by The Wisedude on 2007-07-04
Beryl is working fine, but they SkyDome doesn't want to change. I set it to this picture

[http://www.gnome-look.org/content/show.php/LIF+-+BERYL+animated+skydome?content=55546](http://www.gnome-look.org/content/show.php/LIF+-+BERYL+animated+skydome?content=55546)

And I change the settings (Desktop > Desktop Cube > Skydome > Upload Image)

But it doesn't change , its still the gradient.. Anyone know how?

 PS. I saved the image as .png.

---

### Post by Orb!ter on 2007-07-04
What type of Video Card do you have? It is likely that your card doesn't support the appropriate technology (my ATI Radeon 7500 doesn't).

---

### Post by koshari on 2007-07-04
the skdome image needs to be a certain size image for some reason

i cant rememver the size now, but its like 520*1080 1080*2060 ect.

---

### Post by koshari on 2007-07-04
> It is likely that your card doesn't support the appropriate technology (my ATI Radeon 7500 doesn't).

i really doubt it would be the video card if the rest of the stuff works.....


PaulFXH said on February 10th, 2007, 02:09 PM

> I managed to get a picture on the skydome after I read that the image must have a width:height ratio of 2 and also that the number of pixels in both the width and height must be an integer power of two.

So I used Photoimpression to edit one of my photos to 2048 pixels (width) x 1024 (height) in PNG format and this worked perfectly.

---

### Post by The Wisedude on 2007-07-05
Thanks! I changed it to that size. Works perfectly now! Thanks.

---

### Post by Chymera on 2007-07-21
10x for pointing out the dimention requirements, i figured it was something like this but i couldnt guess xactly what the dimensions should look like.

Anyway, I have a 1280x1024 desktop, so a 2048x1024 pic would look really crappy as an animated skydome (the option which makes it look like its you and not the cube thats moving). So i tried 4099x2048, 4096 = 2 * 2048 and both are of the form 2^n ... still, no output :( could it be that the image is too large? and if its too large shouldnt it actually try to render it first and then crash?

Is there any way around this?

---

### Post by Chymera on 2007-07-24
Anyone?

---

### Post by Afkpuz on 2007-08-02
When you hover over the "pick a skydome picture" box, the tooltip tells you that the dimension must be a power of two.  So here are possible dimensions:

512
1024
2048
4096


any combination of these numbers will work.  However, it doesn't seem that different dimensions do anything.  For example, my screen res is set to 1680x1050.  I experimented with skydomes at 2048x2048   and  1024x2048.  Both resolutions look exactly the same.  So make sure that the image format is .png and that the resolution for both dimensions of the image is to the power of 2.

---

