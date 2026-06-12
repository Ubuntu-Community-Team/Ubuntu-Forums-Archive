---
title: "[SOLVED] nvidia sound card problem"
date: 2008-12-29
forum: General Help
---

### Post by orlox on 2008-12-29
Hi!

I have an hp pavilion from the dv6000 series (more precisely, a dv6439nr) and I cant get sound to work. By checking the sound card, I can see this:

```

pablo@warifaifa:~$ lspci -v | grep Audio
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

```

Also, aplay -l gives this:

```

pablo@warifaifa:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

The thing is, I installed intrepid using the server edition, and then installed the ubuntu-desktop package, together with a lot more stuff. I dont know if this works out of the box on intrepid desktop, and cant check it cause I dont have an intrepid disk at hand...

Any idea to fix this???

---

### Post by gettinoriginal on 2008-12-29
An excellent sound/video troubleshooting site:  :P

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by orlox on 2008-12-29
Thats more like a guide on installing different multimedia packages. Didnt found anything that could help me fix my issue....

---

### Post by gettinoriginal on 2008-12-29
Then I don't understand what your problem is, as alsa and pulse work with your card to make sound work.  I also had no sound, and that page got me there.  :P

---

### Post by orlox on 2008-12-29
Well, I looked on that post, and the only troubleshooting for the no-sound problem was to install the alsa-oss package, but this didnt work for me :(

Was this the thing you tried to fix your sound?

---

### Post by gettinoriginal on 2008-12-29
I did the whole thing, alsa, pulse, pulse audio device, don't know that it's helpful, but after I finished, I had sound.

---

### Post by orlox on 2008-12-29
pulse?? That thread doesnt seem to mention something about pulse...Besides, going over all the steps described there would get me with A LOT of things I dont need installed on my computer :(. But I dont see anything there besides the installation of alsa-oss that could be related to my problem...

---

### Post by gettinoriginal on 2008-12-29
I am so sorry, I thought I had posted this site:  :confused:

[http://ubuntuforums.org/showthread.php?t=997506ttp://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=997506ttp://ubuntuforums.org/showthread.php?t=843012)

---

### Post by orlox on 2008-12-29
That did it! thanks!

---

