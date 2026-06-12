---
title: "Need DVD playback help"
date: 2006-05-28
forum: Desktop Environments
---

### Post by brandt on 2006-05-28
Hey all,
I just installed a fresh copy of ubuntu/kubuntu-desktop on my home system.  I have libdvdread3 and libdvdcss2 installed, but when I hit "play DVD" in kaffeine, the dvd spins up and the read light comes on for about 20 seconds, but nothing else happens.  DMA is enabled on my dvd-rom and I'm pretty sure it's not a mounting issue since I can mount dvds by hand just fine.  I've tried following some of the tutorials, but most of them say "if you have libdvdcss2, everything should just work".  Can anyone shed some light on how to configure my system to play dvds?  Thanks much.

---

### Post by vidak on 2006-05-29
do other players like xine/mplayer play dvd?

---

### Post by brandt on 2006-05-29
I just tried xine, it sort of plays the dvd but drops a lot of frames.  I ran xine-check and it says my server doesn't support YV12 overlays or Xvideo.  I tried to compile xine-lib but I got the error 
```

xine_decoder.c:318: error: 'MAD_OPTION_IGNORECRC' undeclared

```

---

### Post by gingermark on 2006-05-30
Which graphics driver are you using? Do other videos (xvid / mpg etc) play fine, or are they also choppy? What graphics card do you have?

---

### Post by brandt on 2006-05-31
The one avi file I tried didn't seem to be choppy, but I didn't watch it for too long since the sound wasn't working.

---

### Post by gingermark on 2006-05-31
I think your xine problem is related to your graphics driver, which is why I asked what kind of card and what driver you are using. I'm not sure if this is also the cause of the DVD playing problem, but I suppose it is possible. 

For example, I have an nVidia graphics card. Xine is almost useless using the Vesa driver, but it great using the official driver. This is the problem that xine-check was throwing up.

So my advice would be to sort out your graphics driver problem first, and then see if you still have the DVD playing problem.

If you happen to have an nVidia card do
```
sudo apt-get update
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```
and reboot.

If not, post what you do have here, and we'll see what we can do.

If you give more details I'm sure we can help you sort out your sound trouble too.

---

### Post by brandt on 2006-06-03
Thanks.  That did the trick.

---

