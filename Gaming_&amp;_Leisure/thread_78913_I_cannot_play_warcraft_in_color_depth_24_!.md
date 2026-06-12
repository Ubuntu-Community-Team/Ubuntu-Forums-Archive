---
title: "I cannot play warcraft in color depth 24 !"
date: 2005-10-19
forum: Gaming &amp; Leisure
---

### Post by hualala on 2005-10-19
I used to run warcraft III (Frozen throne) through cedega in hoary. It ran well and fluently.
Now I update to breezy,install the nvidia driver and nividia-glx,and enable the opengl support.
then I type this :
```
bwl@bwl:~/war3/war3$ cedega Frozen\ Throne.exe -opengl -window
```
The warcraft lanuchs normally,it looks good.
but when I load a game (combat with computer:p ) or watch replays,
It stops when it is loading.The hard disk lamp stays red and the screen freezes for a  while ,then the game crashs,leaving this in command line:
```
bwl@bwl:~/war3/war3$ mmtime pid=8332 tid=8353
```
**But,when I modify the xorg.conf,set the default color depth to 16,the game can load and i can play though not fluently as in hoary**
some useful info :
breezy 2.6.12-9-686
cedega 4.4
warcraft III Frozen Throne 1.20
nvidia
two attachments:
the jpg is the screenshot when the warcraft crashs
the txt is my xorg.conf

Thank you for reading my post.

---

### Post by 5hundy on 2005-10-20
Hmmmm. I'm not really sure what the issue is, but for kicks you may as well look at your ~/.transgaming/user.reg

Mine contains the following (which I had to manually change to get my widescreen monitor to work):

```

[Software\\Blizzard Entertainment\\Warcraft III\\Video] 1129787955
"adapter"=dword:00000000
"animquality"=dword:00000002
"cinematicbpp"=dword:00000020
"cinematicheight"=dword:00000258
"cinematicoverrides"=dword:00000000
"cinematicrefresh"=dword:0000004b
"cinematicwidth"=dword:00000320
"colordepth"=dword:00000020
"gamma"=dword:00000031
"lights"=dword:00000002
"lockfb"=dword:00000001
"miplevel"=dword:00000000
"modeldetail"=dword:00000002
"occlusion"=dword:00000001
"particles"=dword:00000002
"refreshrate"=dword:0000003b
"resheight"=dword:0000041a
"reswidth"=dword:00000690
"spellfilter"=dword:00000002
"texcolordepth"=dword:00000020
"texquality"=dword:00000002
"unitshadows"=dword:00000001

```

This one is set to x020 or 32-bit color. I also run wc3 in full screen mode in a new instance of X. My guess is that would not change anything but its worth a try.

---

