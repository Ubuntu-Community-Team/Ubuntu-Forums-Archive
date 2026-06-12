---
title: "Why doesn't Gnome have video wallpaper?"
date: 2007-02-05
forum: Desktop Environments
---

### Post by Brazen on 2007-02-05
It seems now with the XGL rendered desktops that it would be a simple matter to have a looping video as your desktop background (or "wallpaper").  Or am I just not able to find information on this?

---

### Post by shareMenaPeace on 2007-02-05
Nice idea...

With beryl i have preview windows and window overall few with playing video to have a wallpaper or even skydome with video would be awesome :)

---

### Post by Omnios on 2007-02-05
It would be really nice to say set up a matrix like background. Aperently you can with lots of tweeking have a screensaver as a background though its very heavy on the resources. I have been thinking of a web like background for a long time. I asked about having zapping tv run as a background but was told this would require root X which no one seems to want to do.

---

### Post by shareMenaPeace on 2007-02-05
Cool is at least teh way how to watch movies :)

STRG + ALT and then click/hold middle mousebutton to enter a cube constant zoom.

---

### Post by Brazen on 2007-02-05
> **Omnios said:**
> It would be really nice to say set up a matrix like background.
...

Ooh, nice idea.  My thinking was along the lines of a pulsating plasma like background.  Matrix would be cool though.

---

### Post by Brazen on 2007-02-05
> **shareMenaPeace said:**
> Cool is at least teh way how to watch movies :)

STRG + ALT and then click/hold middle mousebutton to enter a cube constant zoom.

Hey that's pretty freaking awesom.

---

### Post by RAOF on 2007-02-06
You already can.  You just need to find xwinwrap, the program that takes a normal window (it generally used xscreensavers) and binds it to the desktop.  Google should give it to you.

---

### Post by mcduck on 2007-02-06
I use 'xwinwrap -ni -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/glslideshow -window-id WID -duration 10 -pan 10 -fade 6 -clip -delay 25000' to run GLSlideshow screensaver as my desktop background :D

Xwinwrap is in Beryl CVS repositories if I remember right.

---

### Post by Brazen on 2007-02-06
ah, ok, thanks RAOF and mcduck.

---

### Post by ardchoille42 on 2007-02-06
I know you canuse a screensaver as the desktop wallpaper in gnome, I wrote a little tutorial on this:

[http://www.gnomehelp.org/pmwiki/pmwiki.php?n=Gnome.ScreensaverAsWallpaper](http://www.gnomehelp.org/pmwiki/pmwiki.php?n=Gnome.ScreensaverAsWallpaper)

Seems it should be easy to loop a video as the wallpaper.

---

### Post by suso on 2007-02-14
Actually, video background has been possible in X windows for over 10 years now.  Your desktop is essentially the root window so you can just send the output of screensavers and video players to the root window.  Gnome has made it harder to do this because nautilus manages the desktop and you have to turn off that feature.  xwinwrap seems to use the proper channels to do this in Gnome, which is good.

So any Vista user who tries to show off their new video background feature, you can tell them to bite you because Linux had that years ago.:popcorn:

---

### Post by Omnios on 2007-02-14
> **suso said:**
> Actually, video background has been possible in X windows for over 10 years now.  Your desktop is essentially the root window so you can just send the output of screensavers and video players to the root window.  Gnome has made it harder to do this because nautilus manages the desktop and you have to turn off that feature.  xwinwrap seems to use the proper channels to do this in Gnome, which is good.

So any Vista user who tries to show off their new video background feature, you can tell them to bite you because Linux had that years ago.:popcorn:


 So what we need is to have a nautilus hack to work when using a ani background for X root.

---

### Post by amadeus266 on 2007-06-13
> **ardchoille42 said:**
> I know you canuse a screensaver as the desktop wallpaper in gnome, I wrote a little tutorial on this:

[http://www.gnomehelp.org/pmwiki/pmwiki.php?n=Gnome.ScreensaverAsWallpaper](http://www.gnomehelp.org/pmwiki/pmwiki.php?n=Gnome.ScreensaverAsWallpaper)

Seems it should be easy to loop a video as the wallpaper.

Your link doesn't work. Please update.
Thanks

---

### Post by inoxllor on 2007-06-13
Check this app:

**[http://3v1n0.tuxfamily.org/pool/feisty/eyecandy/xwinwrap_0.1+cvs20060209_i386.deb]("http://3v1n0.tuxfamily.org/pool/feisty/eyecandy/xwinwrap_0.1+cvs20060209_i386.deb")**

**Description:**    Desktop Background animator :D
                            *xwinwrap* is an app that allows users of xgl to replace
                            a desktop background with a movie or a screensaver

---

### Post by smartboyathome on 2007-06-13
That is what everyone has been recommending. ;)

---

### Post by ubuntu-mike022465 on 2007-07-12
"mcduck: I use 'xwinwrap -ni -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/glslideshow -window-id WID -duration 10 -pan 10 -fade 6 -clip -delay 25000' to run GLSlideshow screensaver as my desktop background

Xwinwrap is in Beryl CVS repositories if I remember right."

This is great, except you have a huge, HUGE number of zombie processes in your system monitor, under the processes tab, if you leave it run for a great length of time. :D  

Not sure if I leave it for too long, my lappy will get up and start walking, going "nnnnnnnnnnnnnnnnnnnn, must have brainnnnn"

---

### Post by Lividity on 2007-08-17
Question: I am currently using this line in my sessions profile.

xwinwrap -ni -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/gleidescope -window-id WID


I would like xwinwrap to cycle through all of my screen savers. Anyone have any idea how to do that?

---

### Post by spupy on 2007-08-17
"mplayer -rootwin -loop 0" does the job for movies and such, but it doesn't work with nautilus desktop and it eats ALOT of cpu resources, at least on my pc.

---

### Post by Trevo_Teh_Nerd on 2007-08-18
Has anyone else had the problem of you icons being covered up by the xwinrap? I'm pretty much a newbie when it comes to linux but I'm learning.

---

### Post by Lividity on 2007-08-23
Yeah, my icons get covered when using screensaver wallpaper.

---

### Post by mcduck on 2007-08-23
> **Trevo_Teh_Nerd said:**
> Has anyone else had the problem of you icons being covered up by the xwinrap? I'm pretty much a newbie when it comes to linux but I'm learning.

That's normal. Nautilus draws your normal wallpaper & icons, and other programs can only draw into window that are either above it (covering your desktop and icons) or under it (so you would not even see that anything is running).

The only way to have both icons and animated wallpaper would be either adding animated wallpaper support to Nautilus, or creating another program that would handle both the animated wallpaper and desktop icons.

Anyway, xwinwrap was originally only a quick hack made for the first Compiz demonstartion, it wasn't supposed to be released for public use. After many people asked the creator about the tool he gave it to Compiz/Beryl people but it isn't developed in any way.

---

### Post by Hmarroqu on 2007-08-27
> **shareMenaPeace said:**
> Cool is at least teh way how to watch movies :)

STRG + ALT and then click/hold middle mousebutton to enter a cube constant zoom.

i would love to knw what your running there, and the hardware, see if i can have something like that. :)

---

### Post by Dark Star on 2007-08-27
Cause runninga video wallpaper would kill low end system .. and you can set wallpaper of video via VLC media player :)

---

### Post by Mobbringer on 2007-09-01
> **Dark Star said:**
> Cause runninga video wallpaper would kill low end system .. and you can set wallpaper of video via VLC media player :)

Don't you need to run VLC in DirectX output to do that? Because I've been trying and it doesn't show the "Wallpaper" choice.

---

### Post by komputes on 2008-04-18
> **Dark Star said:**
> you can set wallpaper of video via VLC media player :)

In windows, not in Linux (yet). There's a few brainstorms for this feature to be added by default.


[http://brainstorm.ubuntu.com/idea/4119/](http://brainstorm.ubuntu.com/idea/4119/)
[http://brainstorm.ubuntu.com/idea/406/](http://brainstorm.ubuntu.com/idea/406/)
[http://brainstorm.ubuntu.com/idea/3682/](http://brainstorm.ubuntu.com/idea/3682/)

---

