---
title: "Ubuntu 8.10 Sound Headache on ASUS M50VM"
date: 2009-02-07
forum: General Help
---

### Post by rferreira on 2009-02-07
Hey there, 

Well I'm pretty new on using Ubuntu but so far it's been a good experience except for one thing, the Sound.

The thing is: I have Ubuntu and Windows Vista installed on the same HD and the strange thing was that the sound only worked on Ubuntu if I booted Vista on the first place then restart and boot Ubuntu. 

So i dug a little more and found a solution that apparently worked that was adding:
```
options snd-hda-intel model=3stack-6ch
```
to the file /etc/modprobe.d/alsa-base

Now there are only two problems that i can't solve:

1st: I can't mute the speakers with the headphones plugged in
2nd: Whenever i'm using the console and hit Backspace on an empty line it always plays a loud "bip" from the speakers

Thank you for your help in advance

---

### Post by rferreira on 2009-02-09
A little help please?

---

### Post by ARam1024 on 2009-02-11
I was having the same problem as you.  I can help with the blip problem, but I'm still can't get my speakers to mute when I plug in headphones.

Look at [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301185").

I also still have some problems with my wireless, which I'm exploring in [this ticket]("http://ubuntuforums.org/showthread.php?p=6718965#post6718965").

---

