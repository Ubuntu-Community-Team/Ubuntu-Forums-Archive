---
title: "help with Compro VideoMate DVB-T3000?"
date: 2006-03-05
forum: Desktop Environments
---

### Post by scotty32 on 2006-03-05
hi, am new to the whole linux thing (after being on Windows for ages)

am trying to to setup my Digital TV card on ubuntu and having problems

i followed the tutorial: [http://www.parker1.co.uk/mythtv_ubuntu.php]("http://www.parker1.co.uk/mythtv_ubuntu.php")

but i seemed to get errors at this point:
```
sudo -s -H
mkdir /root/.tzap
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill > /root/.tzap/channels.conf
```

the error is:

```
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:1882: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory
```


has anyone got a videomate working?

being in the MS mindframe its hard to do stuff (simple installs of software seem to be hard :???: )

the Device Manager shows the card as saa7134 
and i found this page on it: [http://linux.bytesex.org/v4l2/saa7134.html](http://linux.bytesex.org/v4l2/saa7134.html)
but it says the kernal already has it so do i not need to bother?

i have /dev/video0 and /dev/video1/
(i have an ATI AiW and a creative webcam is that them? and which would be which?)

and theres a /dvb/ folder too, with about 5 "adaptor" folders, but i only have 1 DVB card (the compro)

umm i have no idea where am up to and with trying different things i might if missed things out or screwed things up :cry: 

anyone know any VERY simple tutorials? or got any advice?

---

