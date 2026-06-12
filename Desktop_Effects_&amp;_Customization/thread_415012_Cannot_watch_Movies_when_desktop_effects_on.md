---
title: "Cannot watch Movies when desktop effects on"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by chakkaradeep on 2007-04-20
Hi All,

I have found this weird problem. If I enable Desktop Effects, I am not able to see Videos in any of the Movie Players (like Totem,VLC) and I can hear only audio.Once I disable the Desktop Effects, I get the display back.

Wat is happening and how to overcome this ?

Thanks

---

### Post by AusIV4 on 2007-04-20
There are a couple of things that could be happening here. First, there are often problems associated with having video windows be partially translucent, or having the brightness of the window changed. 

If you change the videodriver in your movie player to xshm, the video will change with your window, allowing you to warp the image, make it translucent, etc, however this is typically very graphics and processor intensive, so your computer may not be able to handle it, depending on the hardware setup. In Kaffeine, you change this by going to Settings -> Xine Engien Parameters -> Video -> Beginner tab. It's probably a similar method for totem or VLC.

---

### Post by chakkaradeep on 2007-04-20
> **AusIV4 said:**
> There are a couple of things that could be happening here. First, there are often problems associated with having video windows be partially translucent, or having the brightness of the window changed. 


No. The brightness and other settings are proper. 

I have two Feisty boxes, One fresh install and other upgraded from edgy. This happens in the Fresh Install and not on the upgraded box.

> **AusIV4 said:**
> 
If you change the videodriver in your movie player to xshm, the video will change with your window, allowing you to warp the image, make it translucent, etc, however this is typically very graphics and processor intensive, so your computer may not be able to handle it, depending on the hardware setup. In Kaffeine, you change this by going to Settings -> Xine Engien Parameters -> Video -> Beginner tab. It's probably a similar method for totem or VLC.

I use Gnome so currently using only Totem and VLC and both give same results. I didnt find any settings that correspond to Xine Engine in both Totem and VLC and I also think Totem and VLC does not correspond to Xine Engine.

This is already filed as a [bug in Launchpad]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/102290") - Bug #102290

---

### Post by Campingman on 2007-04-20
I am having the same problem with a new install of Feisty, black video with either beryl or compiz enabled.  Anybody have any suggestions?  It is the same both in Totem and VLC and for any video extension I have tried

---

### Post by Drachen on 2007-04-20
> **chakkaradeep said:**
> Hi All,

I have found this weird problem. If I enable Desktop Effects, I am not able to see Videos in any of the Movie Players (like Totem,VLC) and I can hear only audio.Once I disable the Desktop Effects, I get the display back.

Wat is happening and how to overcome this ?

Thanks

Same problem here :( 

And with a fresh installation of Feisty,,,

---

### Post by pt123 on 2007-04-20
[http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#Opening_too_many_windows_leaves_some_of_them_black](http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#Opening_too_many_windows_leaves_some_of_them_black)

Try these work arounds.

---

### Post by Campingman on 2007-04-20
> **pt123 said:**
> [http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#Opening_too_many_windows_leaves_some_of_them_black](http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#Opening_too_many_windows_leaves_some_of_them_black)

Try these work arounds.

Thanks, I will give it a look, I have an ATI card so maybe no good

---

### Post by chakkaradeep on 2007-04-20
> **pt123 said:**
> [http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#Opening_too_many_windows_leaves_some_of_them_black](http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#Opening_too_many_windows_leaves_some_of_them_black)

Try these work arounds.

Am not using Beryl,only Compiz, the default desktop effects and no nVidia too. Its just a normal Intel 82852/82855 GM/GME/PM/GMV Processor.

Only the video (in movies) is black !

Does anybody have solution ?

---

### Post by CarpKing on 2007-04-20
Xvideo (the default output module) conflicts with compositing.  In VLC you can set the module to X11, but that uses a lot of CPU and doesn't look good in fullscreen (somewhere there is a Gstreamer preference for this, which would do the same for Totem).  To keep using Xvideo, you can install mplayer and/or GXine, as they seem to play nicer than Totem or VLC.

---

### Post by Solicitous on 2007-04-20
If you load a terminal and do a;
$ gstreamer-properties
in the Video tab there is a drop down box for Plugin.  I had a similar issue and selected "X Window System (No Xv)" and that solved my issue.

Cheers,

---

### Post by chakkaradeep on 2007-04-20
> **Solicitous said:**
> If you load a terminal and do a;
$ gstreamer-properties
in the Video tab there is a drop down box for Plugin.  I had a similar issue and selected "X Window System (No Xv)" and that solved my issue.


Thanks, that worked for Totem :) 

Any idea how to do this on VLC ?? :(

---

### Post by Campingman on 2007-04-21
Thanks that works great for Totem ( a poorer picture quality than Edgy though).  Gxine also plays the movies OK.
 I also cannot find a setting for VLC. 
 I have an issue with mplayer, error selecting -vo device.  I always get this error with mplayer I did in my last install of edgy and never did sort it out, I have tried all of the vo devices listed ang just cannot get it to work, the Firefox plugin works fine though?

---

### Post by Campingman on 2007-04-21
Quick update
In VLC if you go to settings/preferences/video/output modules click advanced options you can change the video output, I have tried X11 video output and Xvideo extension video output, both now display the video in VLC (a bit choppy though)
Still would like some suggestions for mplayer

---

### Post by chakkaradeep on 2007-04-21
Thanks CampingMan, got it :)

---

### Post by iffans on 2007-04-21
That worked for me too for Totem! Thanks! Is there any disadvantage about disabling Xv?

---

### Post by chakkaradeep on 2007-04-21
> **iffans said:**
>  Is there any disadvantage about disabling Xv?

No idea dude. I am happy that the video works :)

---

### Post by Forceflow on 2007-04-21
Video Playback with VLC on X11 still is slightly blocky, though. You can spot the difference easily.

The pixels just pop out more.

---

### Post by sero on 2007-04-24
For me the solution in VLC was to go to Settings->Preferences, then choose Video and uncheck "Overlay video output". Now video plays fine and only blacks out when dragging the window.

---

### Post by CarpKing on 2007-04-24
> **iffans said:**
> Is there any disadvantage about disabling Xv?

IIRC, when Xv is disabled, the video lacks interpolation (doesn't scale well) and uses the CPU instead of the graphics card.

---

### Post by chakkaradeep on 2007-04-24
> **sero said:**
> For me the solution in VLC was to go to Settings->Preferences, then choose Video and uncheck "Overlay video output". Now video plays fine and only blacks out when dragging the window.

The above solution doesnt work here :(

---

### Post by arish on 2007-05-02
Guys same problem here, video playback is totally damaged when my desktop effects are on. Once i turn them off everything comes back to normal! The solutions mentioned above, despite that solve the problem, i am getting really bad video quality so i dont like them.

is it likely to getting an update for this bug in the near future?

---

### Post by RSrealo on 2007-12-03
I had similar experience running vlc after I installed Beryl and enabled desktop effects. 

I am a newbie using linux and I am loving everything in linux even with some of the bugs. 

Anyways, I uninstalled Beryl using synpathic then went back to desktop effects screen (System>Preferences>Desktop Effects) click the Enable Desktop Effects without selecting any options and it work for me :). I can now use my lovely VLC minus the black-screen.

---

