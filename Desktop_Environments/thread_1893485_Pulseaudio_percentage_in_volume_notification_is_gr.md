---
title: "Pulseaudio percentage in volume notification is greater than actual percentage"
date: 2011-12-10
forum: Desktop Environments
---

### Post by jeremija on 2011-12-10
When I use XFCE4's mixer plugin (a panel applet) and choose the Pulseaudio as soundcard and when I use the mousewheel to adjust the volume, the volume bar width doesn't match the real percentage (in tooltip):

[img]http://www.deviantpics.com/images/st8OA.png[/img]

Is anybody else experiencing this problem?

---

### Post by jeremija on 2011-12-23
Just sharing a solution:

Not sure what happens in gnome, but I solved my problem after reading this post:

[http://ubuntuforums.org/showpost.php?p=8614876&postcount=3](http://ubuntuforums.org/showpost.php?p=8614876&postcount=3)

> 1. sudo gedit /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common
2. Go to the block titled "[Element PCM]" and change the line "volume = merge" to "volume = ignore"
3. Reboot (restarting PulseAudio isn't enough) 

Restarting PulseAudio without rebooting worked in my case.

PulseAudio has an algorithm to control both Master and PCM volume with a single volume control and it is defined in that file. I set it to ignore my PCM channel and set it manually via alsamixer.

---

