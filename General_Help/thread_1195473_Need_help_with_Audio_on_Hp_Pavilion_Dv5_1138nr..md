---
title: "Need help with Audio on Hp Pavilion Dv5 1138nr."
date: 2009-06-23
forum: General Help
---

### Post by Jayishkohl on 2009-06-23
Hello, first off i'd like to say i'm a noob to ubuntu and all linux for that matter, but i'm absolutely loving it thus-far and am excited to get more familiar with it. Ok i've just installed Ubuntu 9.04 on my Hp Pav dv5, and the audio doesn't work. I've looked at a few forums already and can't figure out how to fix this, i;ve checked all the obvious things, and followed a few fixes, like the sudo's. If anyone could help me figure this out it would be greatly appreciated. Sorry for being such a nub. =D

Heres a little more info if this helps,

[http://www.alsa-project.org/db/?f=1c...713621383acea9]("http://www.alsa-project.org/db/?f=1cb3cfb5f10d03d5eb173b6d47713621383acea9")

if you need me to answer any questions just post i'll post back imediatly. Thank you Ubuntuforums.

---

### Post by ed021990 on 2009-06-23
Hi Jayish 

go into ur terminal and type:

sudo gedit /etc/modprobe.d/alsa-base.conf

and get back to me

this is probably just a simple matter of copying and pasting

---

### Post by ed021990 on 2009-06-23
try typing into command:

sudo gedit /etc/modprobe.d/alsa-base.conf

if ur using kubuntu instead, use nano instead of kde, (dont ask me why)

and paste the following to the bottom
options snd-hda-intel model=hp-dv5

---

### Post by Jayishkohl on 2009-06-24
hey ed021990

thank you i did type it in and it brought up the edit window, where do i go from here??

---

### Post by ed021990 on 2009-06-24
ok, scroll down to the bottom of the page in the terminal and paste in 

"options snd-hda-intel model=hp-dv5"  without the quotes

let me know if this worked for u

---

