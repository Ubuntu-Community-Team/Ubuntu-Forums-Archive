---
title: "Kaffeine Player - DVB Question"
date: 2006-07-29
forum: Desktop Environments
---

### Post by FusionXN1 on 2006-07-29
Not sure if this thread belongs in here, but I have Kaffeine Player, My TV tuner (I'll state my tuner for searching reference - KWorld T-100) works out of the box :) Needed xine extra codecs for audio but now I am currently using a DVB-T transmitter that is a little too far away from me, resulting in me only receieving 9 TV Channels - i should / can get around 60 - 80 on my local transmitter but the one closest to me isn't listed. I know the information for it and my question is: **how do I add my transmitter to the Kaffeine Player list?**

I'm not sure what and where to edit. Thanks :)

---

### Post by darkteckno on 2006-09-20
Try asking here: [http://tech.groups.yahoo.com/group/KWORLD-TV/](http://tech.groups.yahoo.com/group/KWORLD-TV/)

---

### Post by mtron on 2006-10-10
really long time ago, but for others:

go to ~/.kde/share/apps/kaffeine/dvb-t/*uk-Transpondername*

the example for eg. Oxford is:

# Oxford
# T freq bw fec_hi fec_lo mod transmission-mode guard-interval hierarchy
T 578000000 8MHz 2/3 NONE QAM64 2k 1/32 NONE

---

### Post by puccaso on 2007-03-11
ok


kaffeine wont find my device in user
but will find it fine in root

why is that?

---

### Post by mtron on 2007-03-30
check that the permissions for /dev/dvb are set to 755, and frontend0, demux0 ect. should be 660

If the permissions were wrong you can e.g. run a small init.d script tat sets them correctly @ boot time

---

