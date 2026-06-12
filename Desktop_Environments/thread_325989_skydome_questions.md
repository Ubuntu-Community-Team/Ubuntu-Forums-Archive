---
title: "skydome questions"
date: 2006-12-26
forum: Desktop Environments
---

### Post by dbbolton on 2006-12-26
i have an image (png) set as my skydome, but all beryl displays is plain white. also, my top cube cap is blank while the bottom one is default, even though i set i different image for them. i "refresshed" and "saved settings" before taking these screenshots.

---

### Post by StarsAndBars14 on 2006-12-26
I've been trying to get my sky dome looking like that for a heck of a long while but it never zooms out enough, and only on rotation.

What do I click, if you could be so kind as to let me know?

---

### Post by nalmeth on 2006-12-26
Your skydome has to be at resolutions of exaclty 2^x

512, 1024, 2048, etc

The ratio isn't the important part, it just has to be 2^x. Also, the greater the size, the better your video card must be to display it. 

The top image is a funny one, I don't have an answer. I set a different one time, and just randomly some time later it finally appeared.

EDIT: Since the top image is blank, it must have tried your image and failed. Go into the settings manager, and make sure "Scale top image" is checked or enabled.

---

### Post by nalmeth on 2006-12-26
>  What do I click, if you could be so kind as to let me know?Beryl-Manager icon in system tray, then Beryl Settings Manager. All the options are in there.
EDIT: By default, hitting cntl-alt and mouse-button one should zoom out and let you control the cube, but anyway, you can configure all that in the Beryl Settings Manager.

---

### Post by StarsAndBars14 on 2006-12-26
Ah!  Got it.  All I had to do was click rotate -> zoom before rotate.

---

### Post by dbbolton on 2006-12-26
> **nalmeth said:**
> Your skydome has to be at resolutions of exaclty 2^x

512, 1024, 2048, etc

The ratio isn't the important part, it just has to be 2^x. Also, the greater the size, the better your video card must be to display it. 

The top image is a funny one, I don't have an answer. I set a different one time, and just randomly some time later it finally appeared.

EDIT: Since the top image is blank, it must have tried your image and failed. Go into the settings manager, and make sure "Scale top image" is checked or enabled.
the original image is 4000x2000

does that mean that i just have to make it like 2048x1024 ?

---

### Post by dbbolton on 2006-12-26
also, i cleared the skydome image with the nifty little broom button, to see if i could just use the gradient, and it was still plain white.

---

### Post by nalmeth on 2006-12-27
> the original image is 4000x2000

does that mean that i just have to make it like 2048x1024 ?
Yeah, try that and if it still doesn't work, cut it down until it does.
The GIMP can do this easily, just IMAGE -> SCALE IMAGE..
So long as it certainly is a png it should work.

You may consider just cropping out a portion of it to 1024x1024 if it comes to that.

---

### Post by dbbolton on 2006-12-27
it's an equiangular photo, so it might look weird if i crop it :/

i restarted X, tried 2048x1024 to no avail. black background that time. but the gradient colours are working now.

---

### Post by mcduck on 2006-12-28
The actual limit how big the image can be depends on how big textures your graphics card can handle. If 2048x1024 doesn't work, try 1024x1024. If you are using animated skydome it's ok to resize the image so that it's proportions get distorted, as when you use it with skydome it will anyway get stretched to fit the spherical skydome.

Also, with image that big you'd probably get nicer skydome by slightly scaling the image bigger, into 4096x2048. The difference to original size is so small that this scaling wouldn't really show in the image quality, but you'd get much higher resolution texture for your skydome.. (if your graphics card can load that big textures)

---

### Post by dbbolton on 2006-12-28
it's an nVidia GeForce 4. i know nothing about graphics cards :D

---

### Post by siman on 2006-12-30
For me the gradient colors work, but I just cant get the skydome image to display.

I tried image sizes 1024x1024, 2048x1024 and 4096x2048 .. beryl just keeps displaying the color gradient. I'd love a skydome :-(

edit: I've got a pretty new GFX card with at least 128 MB

edit2: fixed. i feel stupod: [http://ubuntuforums.org/showpost.php?p=1943922&postcount=2](http://ubuntuforums.org/showpost.php?p=1943922&postcount=2)

---

### Post by dbbolton on 2006-12-30
> **siman said:**
> For me the gradient colors work, but I just cant get the skydome image to display.

I tried image sizes 1024x1024, 2048x1024 and 4096x2048 .. beryl just keeps displaying the color gradient. I'd love a skydome :-(

edit: I've got a pretty new GFX card with at least 128 MB

edit2: fixed. i feel stupod: [http://ubuntuforums.org/showpost.php?p=1943922&postcount=2](http://ubuntuforums.org/showpost.php?p=1943922&postcount=2)
my svg/png boxes are already checked :/

---

