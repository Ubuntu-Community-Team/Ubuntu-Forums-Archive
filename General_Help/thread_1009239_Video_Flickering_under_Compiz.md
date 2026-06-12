---
title: "Video Flickering under Compiz"
date: 2008-12-12
forum: General Help
---

### Post by saifman on 2008-12-12
Hi

I am running Ubuntu 8.10 on a Toshiba A305 laptop with 3GB ram, and ATI mobility graphics HD3470 graphics card and the latest ATI drivers. I am using Ubuntu 8.10 - and the Compiz Window manager

Compiz has been working great except for the fact whenever I am running it and want to play videos using Totem, or want to use Visualisation in Rythmbox, the video flickers; it comes in and then out.

Also if I want to use 3D software such as Xtraceroute, the Globe flickers.

If any body can tell me how I can fix this?
right now I use Metacity and turn off Visual Effects to watch video.

Thanks a lot

---

### Post by sierd on 2009-01-03
I have a toshiba a210-10y ati hd2400 mobile and I had the same problem and I landed on the installation of compiz fusion :D:D:D:D:D:D:D

---

### Post by Eddie Wilson on 2009-01-03
The problem is compiz fusion. It is very unstable and plays havoc with video playback and 3d games. That's one of the reasons that the project is in so much trouble now. Development has stopped and people are leaving.

---

### Post by stderr on 2009-01-03
What you'll find, as sierd implies, is that if you install fusion-icon

```
sudo apt-get install fusion-icon
```

and launch the icon

Applications -> System Tools -> Compiz Fusion Icon

you'll get another blue icon in your system tray. You can right click that icon, click Select Window Manager, and click Metacity. This will change your Window Manager from Compiz to Metacity (a much simpler, smaller WM).

I tend to do this: when not doing anything special, I enable Compiz (with fusion-icon). This gives me all my nice Compiz tools (such as enhanced zoom, 3d cube, etc). When I'm about to do something vaguely graphically involved, I enable Metacity (with fusion-icon) to ensure Compiz won't screw things up.

Alternatively, you can disable the flickering in VLC when Compiz is running by selecting a different video output, although some of the alternatives will tend to increase CPU usage quite a bit. To try this, in VLC, goto Tools -> Preferences -> Video (on left) and set Output to X11.

---

### Post by |{urse on 2009-01-03
easy, open a terminal

> 
gstreamer-propertiesthen click the Video tab and select (No Xv) from the first dropdown menu titled Plugins.

then give it a ctrl + alt + backspace and everything should be cool. 

I tried the Vlc way described above and that works too.

---

### Post by stderr on 2009-01-03
> **|{urse said:**
> > gstreamer-properties then click the Video tab and select (No Xv) from the first dropdown menu titled Plugins.

Exactly what I was trying to remember :D another post-it note goes up on the wall...

---

### Post by binbash on 2009-01-04
for video flickering , set your video player's output to X11

---

### Post by brunolabs on 2009-01-04
> **binbash said:**
> for video flickering , set your video player's output to X11


It doesn't work with a lot of ATI cards.

---

