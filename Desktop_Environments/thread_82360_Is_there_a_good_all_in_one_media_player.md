---
title: "Is there a good all in one media player?"
date: 2005-10-26
forum: Desktop Environments
---

### Post by ztrek7 on 2005-10-26
You know, handles all video, dvd, integrates with firefox (read awesome howto to get mplayer working, check howto section for it), all music, burn cd's, dvd's, vcd's, etc, organizes a library and sorts it for easy access?

If there is one, and I don't know about it, someone let me know! (and point me to the howto or create one!)

Thanks,

---

### Post by soul_rebel on 2005-10-26
totem plays almost anything and integrates with mozilla. 

Integrated music-only cd burning is a feature of amarok and lsongs. (qt - kde programs) Perhaps try kaffeine too.

---

### Post by bathini on 2005-10-26
I am not so sure with totem because it does not play .asx files which is not good. Mplayer either is not good enough. I would say install the whole lot.

bathini

---

### Post by mostwanted on 2005-10-26
I mostly get by with totem-xine

---

### Post by Kyral on 2005-10-26
Totem-Xine and VLC Combined do whatever I want :D

---

### Post by Moonbuzz on 2005-10-26
Can one run Amarok under regular Ubuntu?

---

### Post by Dr. Nick on 2005-10-26
[QUOTE=Moonbuzz]Can one run Amarok under regular Ubuntu?[/QUOTE]


Yes, but the only way ive had sucess is by compiling it manually, the version in the repositories never have worked good for me. You need to install a bunch of kde stuff first though. 

HOWTO for building
[http://ubuntuforums.org/showthread.php?t=80492](http://ubuntuforums.org/showthread.php?t=80492)

---

### Post by angrykeyboarder on 2005-10-26
[quote=Dr. Nick]Yes, but the only way ive had sucess is by compiling it manually, the version in the repositories never have worked good for me. You need to install a bunch of kde stuff first though. 

HOWTO for building
[http://ubuntuforums.org/showthread.php?t=80492]("http://ubuntuforums.org/showthread.php?t=80492")[/quote]

The version in the repositories has worked beatuifully for me both under Hoary and Breezy.

However, I've also always had KDE installed (not that that should make a difference).

---

### Post by angrykeyboarder on 2005-10-26
[quote=ztrek7]You know, handles all video, dvd, integrates with firefox (read awesome howto to get mplayer working, check howto section for it), all music, burn cd's, dvd's, vcd's, etc, organizes a library and sorts it for easy access?

If there is one, and I don't know about it, someone let me know! (and point me to the howto or create one!)

Thanks,[/quote]

Heck, I don't know of one for Windows that covers everything on your list there. LOL.

Totem-xine does everything there but the media burning and it doesn't have the old-fashioned butt-ugly GTK1 interface that Mplayer has.

---

### Post by flower on 2005-10-26
have a look at this feature list: [http://www.videolan.org/vlc/features.html](http://www.videolan.org/vlc/features.html)

this player has also a deb repos so you don't have to compile anything by hand :)

---

### Post by Dr. Nick on 2005-10-26
I dont know of any all-in-one, personally I like having seperate music/video players just so that they are better at one thing and don't try to do to much.
Their are several good apps for organizing music like amaroK and quod libet.

Dont know of any video organizers though


[QUOTE=angrykeyboarder]The version in the repositories has worked beatuifully for me both under Hoary and Breezy.

However, I've also always had KDE installed (not that that should make a difference).[/QUOTE]

The repo version kept locking my computer when I did some things. This is without kde installed, If your in KDE it may run better, all of my attempts have been from gnome.

---

### Post by angrykeyboarder on 2005-10-26
[quote=flower]have a look at this feature list: [http://www.videolan.org/vlc/features.html]("http://www.videolan.org/vlc/features.html")

this player has also a deb repos so you don't have to compile anything by hand :)[/quote]

I didn't know VLC was able to burn media.  Hummm..

Speaking of VLC. I'd tried it several years ago. I can't recall why, but I didn't care much for it.  Then a year or so ago I gave the Windows version a try and it was OK.  I was mostly curious as (at that time) I'd not used any Windows open source software.

Recently I thought I'd give it another shot.  I'd seen screenshots of the program and found the interface to be improved since the switch to wxWidgets.  So I installed the version in the Ubuntu repository.

However....  when I installed it it came up with this ugly-ass GTK1 interface and I'll be damned if I can figure out why.  In the screen shots on the VLC website it doesn't look that way.

---

### Post by Dr. Nick on 2005-10-26
[QUOTE=angrykeyboarder]
However....  when I installed it it came up with this ugly-ass GTK1 interface and I'll be damned if I can figure out why.  In the screen shots on the VLC website it doesn't look that way.[/QUOTE]

[http://ubuntuforums.org/showthread.php?t=76440&highlight=vlc+gtk2](http://ubuntuforums.org/showthread.php?t=76440&highlight=vlc+gtk2)

I think it boils down to the "all free software" mottto of Ubuntu, I havent used vlc yet but it looks like if you can get the previous .0.8.2 you can get gtk2

---

### Post by angrykeyboarder on 2005-10-26
[quote=Dr. Nick][http://ubuntuforums.org/showthread.php?t=76440&highlight=vlc+gtk2]("http://ubuntuforums.org/showthread.php?t=76440&highlight=vlc+gtk2")

I think it boils down to the "all free software" mottto of Ubuntu, I havent used vlc yet but it looks like if you can get the previous .0.8.2 you can get gtk2[/quote] 
Hummm...

I read that thread but I missed any reference to wxWidgets being non-free. I thought it was.  I double checked thier [web site]("http://www.wxwidgets.org") and indeed it's covered under the LGPL......

Speaking of wxWidgets, I've been trying for months to get [a program]("http://sourceforge.net/projects/wxchecksums") to complie under Ubuntu (Hoary and reently Breezy) and Ubuntu never seemed to have the right libraries.

It sounds like this is related to the VLC issue.

---

### Post by Dr. Nick on 2005-10-26
[QUOTE=angrykeyboarder]Hummm...

I read that thread but I missed any reference to wxWidgets being non-free. I thought it was.  I double checked thier [web site]("http://www.wxwidgets.org") and indeed it's covered under the LGPL......

Speaking of wxWidgets, I've been trying for months to get [a program]("http://sourceforge.net/projects/wxchecksums") to complie under Ubuntu (Hoary and reently Breezy) and Ubuntu never seemed to have the right libraries.

It sounds like this is related to the VLC issue.[/QUOTE]

Another thread,
[http://www.ubuntuforums.org/showthread.php?t=75322](http://www.ubuntuforums.org/showthread.php?t=75322)

I think I read it wrong, wxwidgets isnt the problem, I think your right about it being a vlc problem, not sure how hard it would be to run a older version in the meantime

---

### Post by Moonbuzz on 2005-10-26
[QUOTE=angrykeyboarder]Heck, I don't know of one for Windows that covers everything on your list there. LOL.[/QUOTE]
Windows Media Player is supposed to do it all, movies, music, rip and burn.

However, I've been trying all tricks in the book to not use it when I use windowsXP, since that's one bloated, disconfigured piece of shite...
I've used Winamp for music (XMMS in Ubuntu), Windows Media Player 6.4 for movies, DivX player for .avi, and nero for rip'n'burn. Best tools for the job.

Concerning Amarok,
> The version in the repositories has worked beatuifully for me both under Hoary and Breezy.

However, I've also always had KDE installed (not that that should make a difference). But it might. I don't want to start hoarding KDE stuff just to get one piece of software, no matter how good...

---

### Post by Dr. Nick on 2005-10-26
It seems as if banshee (gnome based) will do some of what your looking for atleast for audio

What is Banshee?

Banshee is a music management and playback application for GNOME. Over the course of the year a variety of high quality, highly polished, and all around &#8220;swell&#8221; Mono GNOME Desktop applications have been popping up. As with many of these apps, Banshee has a beautiful user interface and is well architected.

Features:

    * Import CDs
    * Manage your library
    * Play your music
    * Create and maintain playlists
    * Sync music with your iPod
    * Play music directly from your iPod
    * Create audio and mp3 CDs

In short, it does what you need!

[http://www.gnomejournal.org/article/30/the-banshee-music-player-an-introduction](http://www.gnomejournal.org/article/30/the-banshee-music-player-an-introduction)

I may try this one out aswell

Official site
[http://banshee-project.org](http://banshee-project.org)

edit, I cant seem to burn, dont see the option

---

### Post by RAOF on 2005-10-27
I'm not sure about the repo version, but the cvs version I've got of banshee has burning support.  It almost has all the features I want, although some of them don't quite work properly.  It is **not** completely polished - there's quite a lot of stuff which doesn't quite work, or is a little bit ugly :)

---

