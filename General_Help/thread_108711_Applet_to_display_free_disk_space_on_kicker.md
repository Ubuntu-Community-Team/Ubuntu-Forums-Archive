---
title: "Applet to display free disk space on kicker?"
date: 2005-12-26
forum: General Help
---

### Post by Mguel on 2005-12-26
I'm looking for an applet to display free disk space on the kicker (ideally like the mixer applet bars).

I found [free disk space applet]("http://www.kde-apps.org/content/show.php?content=23396") on KDE-Apps, but the link to download is broken. Besides, it seems that it is not too easy to install according to a [Ubuntu post]("http://ubuntuforums.org/showthread.php?t=31415"), considering also that I'm new to linux :rolleyes:.

I'm thinking in installing gDesklets if there is nothing to display that info on the kicker, but I would prefer something more small and lightweight.


**Another small question** conserning applets, I don't know when I lost the volume tray icon to change volume/mute (the one like a small speaker), and I can't find any applet or setting to restore it (maybe it was a gnome thing?). As a workaround I'm using the mixer displaying only the master volume.


Best regards,
Mguel


PS: I'm using **KDE** after installing **Ubuntu 5.10** (removed ubuntu-desktop and xubuntu-desktop after trying them)

---

### Post by Sir_Yaro on 2005-12-28
download it from my site
[http://yaro.gdi.pl/](http://yaro.gdi.pl/)

---

### Post by Mguel on 2005-12-28
Thanks!

It took me a while to find it, but finally donwload it...

Let's see if I can make it work.

Cheers,
Mguel

---

### Post by xtacocorex on 2005-12-28
The speaker in the system tray is a program called kmix.

If you update the sources.list with the ones from [http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html) and then update KDE, there should be a diskspace monitoring applet for kicker installed.

---

### Post by Sir_Yaro on 2005-12-28
LOOOL... Sorry!! I totally forgot that not everybody know polish language... :D:D:D

It too much work to translate all of this to english. I'm to lazy to do that  and my english sucks to much :P

---

### Post by Mguel on 2005-12-28
;)

Just installed it without problems. I have the applet on the kicker but nothing displayed on it, just an empty space :(

On the configuration window on the "Partitions" part, I have it empty too... it seems it doesn't recognize my mounted partitions or something.

---

### Post by Mguel on 2005-12-28
[quote=xtacocorex]The speaker in the system tray is a program called kmix.[/quote] Thanks!

[quote=xtacocorex]If you update the sources.list with the ones from [http://www.psychocats.net/sources.html]("http://www.psychocats.net/sources.html") and then update KDE, there should be a diskspace monitoring applet for kicker installed.[/quote] Thanks!, as free disk space didn't work I'll have a look to your link.

---

### Post by Sir_Yaro on 2005-12-28
add it into down left corner (Attachment). in other places u may not see data.

---

### Post by Mguel on 2005-12-28
[quote=xtacocorex] [http://www.psychocats.net/sources.html]("http://www.psychocats.net/sources.html") and then update KDE, there should be a diskspace monitoring applet for kicker installed.[/quote]
Page not found :(

---

### Post by xtacocorex on 2005-12-28
[QUOTE=Mguel]Page not found :([/QUOTE]

Hmm, must have changed the url, let me find the new one.

Found it: [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by Mguel on 2005-12-28
[quote=Sir_Yaro]add it into down left corner (Attachment). in other places u may not see data.[/quote]

I move it to the left... I made the kicker background solid (not transparent), I made the kicker bigger, I place the kicker at the bottom... but empty....

---

### Post by Mguel on 2005-12-28
[quote=xtacocorex]Found it: [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")[/quote]
Thanks again...

---

### Post by xtacocorex on 2005-12-28
[QUOTE=Mguel]
I'm thinking in installing gDesklets if there is nothing to display that info on the kicker, but I would prefer something more small and lightweight.
[/QUOTE]

Since you're using KDE, I'd get superkaramba instead of gDesklets if you go this route.

---

### Post by Mguel on 2005-12-28
[quote=xtacocorex]Since you're using KDE, I'd get superkaramba instead of gDesklets if you go this route.[/quote]
Good to know ;)

---

### Post by Mguel on 2005-12-28
[quote=xtacocorex]If you update the sources.list with the ones from [http://www.psychocats.net/sources.html]("http://www.psychocats.net/sources.html") and then update KDE, there should be a diskspace monitoring applet for kicker installed.[/quote]
I chequed the page, and I have allready enabled the extra repositories... and my system is "up to date".

What is the name of that applet you mention?

---

### Post by xtacocorex on 2005-12-28
I will check on this when I get home and am not using an XP machine.

Edit:
I was mistaken, I was thinking of kwikdisk which runs in the system tray.

---

### Post by xtacocorex on 2005-12-28
Where did you find the source on his site because I'm lost.
I'm going to try to install it and see why you can't view the mounted partitions.

---

### Post by Mguel on 2005-12-29
[http://yaro.gdi.pl/deb/diskfree_0.15-1_i386.deb](http://yaro.gdi.pl/deb/diskfree_0.15-1_i386.deb)

cheers!

---

### Post by xtacocorex on 2005-12-30
I installed and had the same problem. I read the comments on the kde-apps page and it seems to not be picking up a .desktop file that it's supposed to.

I also wonder if the problem could be that the package for a Debian system and not Kubuntu. I know there is a way to convert it, but I can't find it on the forums.

I'll continue looking.

---

### Post by Omnios on 2005-12-30
[QUOTE=xtacocorex]Since you're using KDE, I'd get superkaramba instead of gDesklets if you go this route.[/QUOTE]

 Ill second SuperKaramba, I have actualy made a full sensor applet with it and counting on what you are using it for it has the smallest footprint of the apps I have tryed so far. It is also easy to script and modify alling for customizazation for your specific needs. Id recomend reading the superkaramba how to web site and go over a few exzisting apps scripts and you will get exactly what you want.

 I had a full sensor suit running at 5 megs of ram and about 2 or 3% cpu.

---

### Post by Mguel on 2006-01-01
I installed superkaramba and have made a text based theme according to what I wanted.

It's very good and flexible. It reminds me of windows Rainmeter which I used when I was in windows.

I would like to use superkaramba 0,37 though, to hide the tray icon, but it's not on the repositories yet, and I have read that there are some dificulties in installing using the debian .deb

Cheers,
Mguel

---

