---
title: "I can't Run Nexuiz in Ubuntu 14 LTS [Help]"
date: 2015-09-09
forum: Gaming &amp; Leisure
---

### Post by rafi_khan2 on 2015-09-09
I have Downloaded Nexuiz-252.zip.
i tried some command
cd ./Nexuiz
./nexuiz-linux-x86_64-sdl
it open a window and show "You have reached this menu duo to missing or unlocatable content/data"
Thats it.
Some one help me please

---

### Post by efflandt on 2015-09-11
I have no idea what **sdl** is, but know what **glx** is, so ./nexuiz-linux-glx.sh works for me in 64-bit Ubuntu 14.04 with nvidia graphics and drivers. The shell script sets some things up (including paths related to where it is run from) and automatically chooses 32 or 64-bit according to your system.

For some reason it was pulled from Steam as a possible future Steam game (maybe lack of further development), but it even works pointing to that script as a non-Steam game. It has wide screen video modes, so I was able to change it to the native resolution of my 1080p HDTV.

PS: ./nexuiz-linux-sdl.sh also works for me.

---

