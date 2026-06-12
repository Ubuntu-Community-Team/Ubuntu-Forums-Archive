---
title: "screen position a few pixels off"
date: 2010-10-24
forum: Desktop Environments
---

### Post by mttolmie on 2010-10-24
In 10.04 on a Shuttle the screen position is a few pixels off.
I fix this with xvidtune for the session. I also get a new modeline.

I build a new xorg.conf file (go virtual terminal, stop gdm, Xorg -configure, etc) and move it to /etc/X11.

I introduce the modeline in the monitor section and reboot (I could do a service gdm stop...).

Guess what, my screen is still a few pixels off. The documentation clearly states that if there is an Xorg.conf, it will be used. So what gives?

This problem has existed since the xorg.conf file was dropped. It is just plain silly that one has to engage in a geeky treasure hunt to correct a few pixels. This adjustment should be present in the System/Preferences/Montors. This is why Linux does not make it with ordinary users, making (superficially) simple things difficult.

By the way, is this the correct forum?

---

### Post by dougalkerr on 2010-10-24
I agree with your sentiments even though I can't help. I have always found that if my screen is off it is the monitor default settings and not the Linux system that is the problem.
Have you tried the default settings using your monitor buttons? I presume you have...

About the simple things being difficult in Linux - yes you are correct in feeling as you do. I have used both Linux and ... ahemmm, Windows for a long time now and Linux is doing very well for a system that is mostly supported by users and not multi-national companies.

There are quite a few areas that Linux excels over the Windows environment because the software and operating system are free to start with. If I was to buy an amplifier for my music system and had to adjust the volume every time I turned it on I would be very frustrated but, if I got a brand new amplifier that did even more than the one I bought and in a better way then I would put up with the odd niggle for the sake of knowing that the people that have built the amplifier and made it available for free have concentrated upon the music reproduction first and foremost. Linux is a little like this but, more importantly all the software tools are available to download and install (if not already available within the built-in packages) to make it possible for you to learn how to make the system perfect for you.

Please be patient, someone more knowledgeable than me will hopefully come to your rescue and keep your experience of Linux pleasant.

---

