---
title: "Making an animated Wallpaper (HTML?)"
date: 2011-10-29
forum: Desktop Environments
---

### Post by MIssigno on 2011-10-29
Hi there!

Sooo, im trying to give some life to my Kubuntu 11.10 Plasma desktop... I'd like to have a nice animation on the background (a slow rain for example).

I tried a lot of things! The closest try was using xwinwrap, a small script to achive this. But nothing...

Is there any way to, for example, set a animated gif as wallpaper? Or maybe a HTML file? 

Thanks in advance!

---

### Post by inobe on 2011-10-29
did a search, even check some stuff on tube, it is out there, just not something by default.

[http://www.google.com/search?client=ubuntu&channel=fs&q=kde+animated+background&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=kde+animated+background&ie=utf-8&oe=utf-8)

---

### Post by EuclidsElements on 2011-10-30
I am very curious about this goo--I would love to be able to drop an animated gif as my background. The video concept from the guy below seems cool, but resource-intensive. Did you try it? Does it affect performance?

---

### Post by |Anthony| on 2011-11-04
I wrote a pretty lengthy bash script (500+ lines) as a frontend for  xwinwrap.  You can set a screensaver or video as your desktop background. It gives  you the  ability to set transparency and and adjust the volume (for  videos)  among lots of other features.  It's called  VDesk and you can get  it for free at [gnome-look]("http://gnome-look.org/content/show.php/VDesk+-+Visual+Desktop?content=141678").

As far as how resource intensive... It really depends on what you're using and the hardware you have. Some screensavers can be a drain as can some videos. VDesk uses MPlayer for video playback. Mplayer allows you to set up hardware acceleration so that really helps. On my HTPC, which has a single core Intel Celeron and a GT240, video playback uses maybe 3% CPU. Not draining at all. Should mention that that is using a 1080 .mkv file. By contrast, my main computer has an Intel E3400 and a GeForce 8600. When using the Helios screensaver, helios uses ~ 12%, Compiz shoots up to ~10% and xorg goes up to about 9%. So when using that hungry screensaver the total cpu usage goes up to about 50% and a 1.00 load (my normal usage without VDesk is ~ 12% and 0.35 load).

Hope that helps answer some questions and give you some options.

---

