---
title: "Dvd"
date: 2006-06-21
forum: Desktop Environments
---

### Post by dareofficer on 2006-06-21
How can I take a AVI, or MPG file and make it into a DVD, that we can watch on a DVD Player?

Thanks

---

### Post by ubuntu27 on 2006-06-22
[QUOTE=dareofficer]How can I take a AVI, or MPG file and make it into a DVD, that we can watch on a DVD Player?

Thanks[/QUOTE]

Run K3B (install it if you don't have it)

And then click on File/New Project/ X

Where X is the action you wanna take, like Burn a DVD (New DVD Project) or make a VCD (New Video CD Project)

now, add your videos that you want burn and then click on "Open the burning dialog" 
Adjust anything you want and then Click on Burn.

Voila!


Note 1: Avi Formats are not supported, so you have to convert them to other formats.

Read this site for instruction on how to convert Video formats: [http://smorgasbord.net/convert_video_linux](http://smorgasbord.net/convert_video_linux)

Note 2: Don't forget to install all the codecs. 

Note 3: Someday you will want to burn MP3, so get MP3 support for K3B by one of the following:

1) Breezy Badger. Install "K3b-mp3" 
2) Dapper Drake. Install "libk3b2-mp3"

You can find those in the repos.

---

### Post by disturbed1 on 2006-06-22
Simple point and click method - install devede, [http://www.rastersoft.com/programas/devede.html]("http://www.rastersoft.com/programas/devede.html") ;) or get the package from [www.debian-multimedia.org]("http://www.debian-multimedia.org") .

A little more involved, install avidemux or tovid

Need full control?

man mencoder
man ffmpeg

---

### Post by dareofficer on 2006-06-22
Thanks, it works great!

---

### Post by ubuntu27 on 2006-06-22
> **dareofficer]Thanks, it works great![/QUOTE]

You're very welcome :)

[QUOTE=disturbed1]Simple point and click method - install devede, [http://www.rastersoft.com/programas/devede.html]("http://www.rastersoft.com/programas/devede.html")  said:**
> www.debian-multimedia.org[/URL] .

A little more involved, install avidemux or tovid

Need full control?

man mencoder
man ffmpeg


Thank you Dist. 1 !! One more app to check it out ;)

---

### Post by DarkDancer on 2006-06-22
Hay, Avidemux is pretty cool, um, how do you get it to burn?

---

### Post by Kouya on 2006-06-24
Hmm i was wondering, would gnomebaker be better than k3b since i use a gnome environment and install k3b would install alot of more kstuff into the comp...

which is a better app?

---

### Post by disturbed1 on 2006-06-24
I wouldn't say one is better than the other ;) It's what better suites your needs. However, if you don't have, nor plan on using any other KDE apps, or the whole KDE enviroment, there really isn't a need to install K3B as it does add a bit of KDE libs that not only get installed, but are also running in the background. It won't cause any problems, but it is un needed bulk if all you want to do is burn an iso. Both Gnome Baker and Nautilus will burn a DVD ISO just fine.

Avidemux doesn't burn, it's more of an editor. You would import your media file, Avidemux would allow you to edit, filter, resize..... then encode to DVD compliant MPEG2 video and ac3 audio. You would then have to author that mpeg2 and ac3 to a DVD using an authoring program like DVD Styler ( [http://dvdstyler.sourceforge.net/]("http://dvdstyler.sourceforge.net/") ) There are .debs on the DVD Styler page that work fine with Ubuntu.

---

### Post by detectiveinspekta on 2006-06-24
I believe they all do the same job, one or the other just provides safer methods of doing it. Burning the acual disk is the easy part, encoding the video and creating the dvd file system is the hard part.

Im currently learning how to create menus and a set of videos on a dvd disk, some of the videos have different aspect ratios and scaled differently and its causing problems. If its one video it's no problem, but I'm not wasting $7 on a DL DVD disk for a few minutes of playback.

Using mencoder to encode, here is how they say to do it, very simple:
[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-vcd-dvd.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-vcd-dvd.html)

Creating the dvd filesystem using dvdauthor (menus etc):
[http://forums.gentoo.org/viewtopic.php?t=117709](http://forums.gentoo.org/viewtopic.php?t=117709)

---

### Post by detectiveinspekta on 2006-06-24
I gota create a howto for this

---

### Post by Kouya on 2006-06-24
i need to copy and burn an iso....for copying someone recommended k9copy which is also a kde app. I need a prog to do general cd and dvd data burning, copy cds and vcd...

does gnomebaker and nautilus handle all these? as well as create iso? they are stable rite? dun wanna have lots of coasters....:p

---

### Post by disturbed1 on 2006-06-24
I've always used Nautilus and GnomeBaker for all of my burning chores. There is also Bonfire, but it may not be considered stable since it's still in alpha/beta stage. I do use Bonfire every now and then, and it works. But it's just easier for me to right-click on an ISO and choose burn to disc right from Nautilus.

Besides K95copy, there is also xDVDShrink. Maybe not as pretty of an interface compared to K95copy, but the end result is the same. xDVDShrink does not require KDELibs, it is written in PERL-Gtk2 for the GUI and bash for the actual work.
[http://dvdshrink.sourceforge.net/](http://dvdshrink.sourceforge.net/)

You can get the .deb from [www.debian-multimedia.com](www.debian-multimedia.com) if you don't want to compile it yourself.

Since you seem hesitant to install KDE libs, I'd give the non KDE apps a try first, if they don't work to your liking, then installing the KDE apps shouldn't cause any problems with stability.

---

### Post by Kouya on 2006-06-24
cool I'll give it a shot but the link foe .deb does not seem to be working.

---

### Post by disturbed1 on 2006-06-24
[quote=Kouya]cool I'll give it a shot but the link foe .deb does not seem to be working.[/quote] 
oops, it .org

[www.debian-multimedia.org]("http://www.debian-multimedia.org")

---

