---
title: "gnome freezes / restarts constantly"
date: 2009-06-14
forum: General Help
---

### Post by Titi on 2009-06-14
Good day!

The last couple of months, I've been annoyed with the following problem:

In the morning, when I boot up my PC, it will freeze just after login, or when I've been busy for about a minute. Alternatively, it restarts just like that, without any warning. Sometimes it happens just once or twice and then I can continue all day without any problems, but sometimes, I have to restart at least 5 times before my system seems to "stabilize". Surely this can not be normal.

I'm not sure, but I think it's somehow related to this system log message (although I don't know what it means):

2009-06-14 09:33:17	blackbird	pulseaudio[12558]	alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
2009-06-14 09:33:18	blackbird	pulseaudio[12558]	alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.

Anyway, I think it has something to do with PulseAudio (which I cannot remove without removing Ubuntu-desktop). So now I'm using KDE, hoping the problem will not show up anymoren.
But I like Gnome more, so I would really like to fix this.

Any ideas?

Thanks a lot!

Maarten

PS: I use ubuntu 9.04, fresh installation, but this problem also occured with previous editions...

---

### Post by gradinaruvasile on 2009-06-14
You can safely remove ubuntu-desktop. Its a metapackage, will not affect anything.
But its enough to disable it.
How to disable pulseaudio:

First open system-preferences-sound
select alsa everyehere

Open system-preferences-sessions
click add
name: kill pulseaudio
command: killall pulseaudio

click add

open a terminal:

sudo gedit /etc/pulse/client.conf

Here find autospawn = yes
change it to 
autospawn = no
save the file.

type

sudo mv /etc/X11/Xsession.d/70pulseaudio ~/

Make sure you have selected the sound devices to alsa.

reboot

U should have only alsa working...

Source to removing pulseaudio:

[http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/")

---

