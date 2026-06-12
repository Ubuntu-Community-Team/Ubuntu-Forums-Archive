---
title: "Nvidia Compiz tearing"
date: 2008-01-18
forum: Desktop Effects &amp; Customization
---

### Post by ear9mrn on 2008-01-18
Hi all,


Here is my problem....

I have a mythtv setup using Ubuntu 7.10. I have a GeForce 7600 GS video card with an optoma projector connected to the hdmi output and a small LCD screen to the vga output. I have set up as a twin view with my menu bars on the small screen to the left and and I have the projector as the screen for my mythtv. 

All works really well except two problem. First is a small gap at the top of the screen when mythfrontend is displayed, for some reason it does not know the size of full screen. Not too bothered about that. More seriously when I play any sort of video, avi or from DVD I get this very annoying tearing of the image. I have played with advance desktop effects and Nvidia-settings without any success (Vblank etc). Nothing seems to solve this problem. It appears the LCD screen and the project have a different horizontal refresh as one seems worse than the other when I move a window around fast.

Any suggestion would be great.

Thanks,

Pete.

---

### Post by FuturePilot on 2008-01-18
Make sure you have SyncToVBlank enabled under both X Server XvVideo Settings and OpenGL Settings.

---

### Post by ear9mrn on 2008-01-20
I solved the problem. Instead of using twin view you need to use Xinerama see picture.
 

[IMG]http://www.nevill.uk.net/bblog/Pictures/ZZ_Misc/Screenshot-NVIDIA%20X%20Server%20Settings.png[/IMG]

---

