---
title: "How To: Install Wolfenstein Enemy Territory in Ubuntu 15.04"
date: 2015-05-29
forum: Gaming &amp; Leisure
---

### Post by Daswebmastri on 2015-05-29
So I enjoy playing ET but ETLegacy keeps giving me errors and was less appealing than the classic so I put together a how-to on getting the old ET to work (with sound) on 64 bit.

Before hand, I may have missed a step or a i386 dependency; these are going on terminal history so please feel free to point out anything I missed. Also, I'm not responsible for anything thing whatsoever that goes wrong with your system, computer, software, etc.

Let me re-type this again for clarification: I AM NOT RESPONSIBLE FOR ANYTHING WHATSOEVER THAT GOES WRONG WITH YOUR SYSTEM, COMPUTER, SOFTWARE, ETC.

Here we go!

1.) Open a browser and a terminal

2.) Head over to [http://www.playdeb.net/updates/Ubuntu/15.04#how_to_install](http://www.playdeb.net/updates/Ubuntu/15.04#how_to_install) and follow the instructions on adding the repo

3.) Update your software list "sudo apt update"

4.) Install classic ET "sudo apt install enemy-territory enemy-territory-data"

5.) Install a lot of i386 dependencies 
"sudo apt-get install libglu1-mesa:i386 libc6:i386 libdrm2:i386 libexpat1:i386 libgcc1:i386 libgl1-mesa-glx:i386 libglapi-mesa:i386 libglu1-mesa:i386 libstdc++6:i386 libx11-6:i386 libx11-xcb1:i386 libxau6:i386 libxcb1:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxshmfence1:i386 libxxf86vm1:i386 libasound2:i386 libasound2-plugins:i386 libstdc++5 libstdc++5:i386 libsdl1.2debian:i386"

6.) Grab the sound fix
"wget -q -O - [http://nullkey.kapsi.fi/et-sdl-sound/et-sdl-sound.gz](http://nullkey.kapsi.fi/et-sdl-sound/et-sdl-sound.gz) | gzip -d > et-sdl-sound && chmod a+x et-sdl-sound"

7.) Move the sound fix so as not to clutter your home folder
"sudo mv et-sdl-sound /home/USERNAME/.etwolf/et-sdl-sound"

8.) Edit your desktop file to point to the sound fix
"sudo gedit /usr/share/applications/enemy-territory.desktop"

change the line that says "EXEC=et" to "EXEC = /home/USERNAME/.etwolf/et-sdl-sound

9.) Save and close.

10.) Go to [http://etkey.org](http://etkey.org) and download a key and run the following: "cp /home/USERNAME/Downloads/etkey /home/USERNAME/.etwolf/etmain/etkey"

11.) Assuming you nor I forgot or missed anything, you should be able to click Enemy Territory from the Dash and play with sound.  

Good luck!

---

