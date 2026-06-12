---
title: "SkyDome Background Image not showing up"
date: 2007-06-22
forum: Desktop Effects &amp; Customization
---

### Post by Christ_Guard on 2007-06-22
Hi guys,
    I am having a problem with my Ubuntu Beryl Skydome Image, It does not show up, I have tried a varity of images, even from the Beryl-themes.org website, yet nothing seems to work, it will change the color of the background, but thats about it. Any Ideas why?

Thanks;
-Christ_Guard

---

### Post by orange2k on 2007-06-22
You might try reducing the image size to something like 1024x512.
Thats how I got it to work on my MX 4000 with 128MB RAM. Bigger sizes don`t work for my system...

---

### Post by bare516 on 2007-06-22
Do you know what kind of video card you have?  If you are running an ATI card, you're SOL.  ATI has poor to no support for Linux.  I have an ATI card installed in my laptop and I have Beryl installed too.  It works but it's not perfect, I don't get all the effects like the "water effect" and SkyDome backgrounds.  When I need to watch podcasts or DVD movies on Totem, VLC, and even Mplayer I get a blank screen but you can hear the audio.  I have to switch from Beryl to Metacity in order to view my DVDs or podcast.  Funny thing, I have Democracy TV installed and it works fine under Beryl.

Anyhow, I have another Ubuntu distro box with a Nvidia card and it works fine.

---

### Post by qamelian on 2007-06-22
> **bare516 said:**
> Do you know what kind of video card you have?  If you are running an ATI card, you're SOL.  ATI has poor to no support for Linux.  I have an ATI card installed in my laptop and I have Beryl installed too.  It works but it's not perfect, I don't get all the effects like the "water effect" and SkyDome backgrounds.  When I need to watch podcasts or DVD movies on Totem, VLC, and even Mplayer I get a blank screen but you can hear the audio.  I have to switch from Beryl to Metacity in order to view my DVDs or podcast.  Funny thing, I have Democracy TV installed and it works fine under Beryl.

Anyhow, I have another Ubuntu distro box with a Nvidia card and it works fine.

You can fix the video playback issue in Totem by running gstreamer-properties and changing the video setting to xv. As for the water effect, it works fine on my laptop with an ATI Mobility Radeon 9000 graphics card, so it's not necessarily an ATI issue. Neither is the video playback issue by the way. I get the same problem on my Nvidia desktop PC until I change gstreamer-properties.

---

### Post by SendDerek on 2007-06-22
I know that I can't change the skydome either on my Intel Graphics, but it works for my other nVidia box.

---

### Post by Ultra Magnus on 2007-06-22
The skydome image needs to have pixels like 1024x1024 - basicallt powers of 2 but they can be different like 1024x512 basically 2^n x 2^m (where n and m are integers)
use gimp to rescale the image to the right size.

---

### Post by Christ_Guard on 2007-06-22
Thanks,
     Changing it to 1024-512 did the trick!

---

### Post by minoas on 2007-06-22
To check your max supported texture size depending on the system use that command in terminal

xvinfo | grep max

For Skydome it has to be 1:2 ratio

---

### Post by ScoPro on 2007-09-10
> **bare516 said:**
> Do you know what kind of video card you have?  If you are running an ATI card, you're SOL.  ATI has poor to no support for Linux.  I have an ATI card installed in my laptop and I have Beryl installed too.  It works but it's not perfect, I don't get all the effects like the "water effect" and SkyDome backgrounds.  When I need to watch podcasts or DVD movies on Totem, VLC, and even Mplayer I get a blank screen but you can hear the audio.  I have to switch from Beryl to Metacity in order to view my DVDs or podcast.  Funny thing, I have Democracy TV installed and it works fine under Beryl.

Anyhow, I have another Ubuntu distro box with a Nvidia card and it works fine.

Try this bare516:

I have an ATI card and no matter what I tried, I couldn't get a skydome image to load... the screen would just go white on me, and no matter what the image size or format I tried, I got the same result. I finally gave up and started looking around for a fix for why my custom trueglass theme was going white when I hit the maximize button, and strangely enough... the fix for that fixed my skydome problem too!!

A big thanx to the people at [http://www.bloglines.com/blog/cybernout](http://www.bloglines.com/blog/cybernout) for helping me figure this out!

gksu gedit /etc/drirc


paste :



<driconf>

<device screen="0" driver="radeon">

<application name="all">

<option name="allow_large_textures" value="2" />

</application>

</device>

</driconf> 

Now just save the file and you'll be off and running.

Hope this helps somebody out there!

(This is the first time I've ever logged a fix on the Ubuntu forums... I'm so excited!)

-ScoPro

---

