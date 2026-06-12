---
title: "Ubuntu 6.06, Morrowind, ATI Radeon Mob. 7500, Cedega"
date: 2006-09-07
forum: Gaming &amp; Leisure
---

### Post by Poldi on 2006-09-07
hi all.

I am trying to play Morrowind (including Tribunal and Bloodmoon) using Cedega 5.2.6 and Ubuntu 6.06 on a Thinkpad (1,4 GHz Centrino, 512 MByte) with an ATI Radeon Mobility 7500.

installation of both Morrowind and the expansions (via Cedega) was uneventfull and successfull.

I tried Morrowind in a resolution of 800x600, no menu-transparency and very limited view-range.

I am using the 'radeon' X11-server cause the ATI binary-drivers only work on Radeon 8500 and up. several options "AGP***" "true" etc. have been tried.

'glxgears -printfps' gets me 920 fps, 'glxinfo | grep render' says direct rendering 'yes' with Mesa DRI. both I consider ok for the graphics card at hand.

the Cedega-settings for Morrowind have been taken from Cedegas own GDDB-database, I later tried to experimentally disable pixel- and vertexshader.

problem at hand: Morrowind runs at 5 sec/frame. that's right, 5 sec/frame, not 5 frame/sec. (would be bad enough...)

it's been some time since I played Morrowind and I remember having the smae problems during the Warty 4.10-time but when I updated to Hoary and changed _something_ the game suddenly ran as fast as in Windows [2000]. I used a time-limited version of Cedega (5.0.1) at that time and thus discontinued gaming.

I can't remember whatever magic I did back then (might have been a setting in either Morrowind or Cedega or my xorg.conf) but now that I have my own registered Cedega 5.2.6 I would like to try again.

anybody out there with similar hardware and a clue?

thanks and regards,
Carsten

---

