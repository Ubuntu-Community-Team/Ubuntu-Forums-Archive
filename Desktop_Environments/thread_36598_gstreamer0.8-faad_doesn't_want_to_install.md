---
title: "gstreamer0.8-faad doesn't want to install"
date: 2005-05-23
forum: Desktop Environments
---

### Post by mellowyllw6 on 2005-05-23
I need AAC support in Rhythmbox, which USED to work, then I tried XMMS, Mplayer, and xine-ui and things got BORKED!

Talk about not fixin' anything that ain't broke, eh?

Anyways, when I try to install gstreamer0.8-faad I get this message:

gstreamer0.8-faad:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed

I can't install 2.3.2.ds1-21 because I can't find it. All I see is 20.

Help?

---

### Post by angrykeyboarder on 2005-05-24
[QUOTE=mellowyllw6]I need AAC support in Rhythmbox, which USED to work, then I tried XMMS, Mplayer, and xine-ui and things got BORKED!

Talk about not fixin' anything that ain't broke, eh?

Anyways, when I try to install gstreamer0.8-faad I get this message:

gstreamer0.8-faad:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed

I can't install 2.3.2.ds1-21 because I can't find it. All I see is 20.

Help?[/QUOTE]

Oh good, it's not just me then.....

I think it's some sort of compatibility issue due to multiple repositories.  I've not had the patience to deal with it further (for the time being).

---

### Post by cinematography on 2005-05-24
I can't get it to work either. :( Ugg... I can't believe such a perfect OS wouldn't have mp3 support?!?  ](*,)

---

### Post by ChinaCatJones on 2005-05-24
I had similar issues with the libc6 depencies.  

It seems to me I resolved them by disabling the unstable marillat repository in /etc/apt/sources.list

After that I did the normal normal apt-get update/upgrade process.

Hope this helps.

Chris

---

### Post by cinematography on 2005-05-24
[QUOTE=ChinaCatJones]I had similar issues with the libc6 depencies.  

It seems to me I resolved them by disabling the unstable marillat repository in /etc/apt/sources.list

After that I did the normal normal apt-get update/upgrade process.

Hope this helps.

Chris[/QUOTE]
How do you do this? I see nothing in that file that says marillat. :(

---

### Post by fng on 2005-05-24
mp3 support is not included in the default install because of legal reasons.

Following the unofficial ubuntuguide and installing gstreamer0.8-plugins, w32codecs, liblame0, and gstreamer0.8-lame_0.8.8-0.1_i386.deb in **this order** should give you mp3 support and a lot more codecs.

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by Burgundavia on 2005-05-24
This error is probably due to using Marilliat repos. I suggest you switch to the hoary-extras one fromt eh backports.

Corey

---

### Post by cinematography on 2005-05-24
[QUOTE=Burgundavia]This error is probably due to using Marilliat repos. I suggest you switch to the hoary-extras one fromt eh backports.

Corey[/QUOTE]
The what?! ](*,) lol

---

