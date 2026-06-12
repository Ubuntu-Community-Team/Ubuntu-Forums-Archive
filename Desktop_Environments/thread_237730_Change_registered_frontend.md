---
title: "Change registered frontend"
date: 2006-08-16
forum: Desktop Environments
---

### Post by carllfo on 2006-08-16
I am trying to use my Nebula Digitv USB with Ubuntu.
I have followed the tutorials and instructions, downloaded the correct firmware etc.

The problem is that the frontend module being loaded is the wrong one (in bold), it should be the mt352 frontend.

I just need to know how to change this, thanks in advance :) 

```
dvb-usb: found a 'Nebula Electronics uDigiTV DVB-T USB2.0)' in warm state.
[17179592.484000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[17179592.484000] DVB: registering new adapter (Nebula Electronics uDigiTV DVB-T USB2.0)).
**[17179592.516000] DVB: registering frontend 0 (NxtWave NXT6000 DVB-T)...**
[17179592.516000] input: IR-receiver inside an USB DVB receiver as /class/input/input2
[17179592.516000] dvb-usb: schedule remote query interval to 1000 msecs.
[17179592.516000] dvb-usb: Nebula Electronics uDigiTV DVB-T USB2.0) successfully initialized and connected.
[17179592.516000] usbcore: registered new driver dvb_usb_digitv
```

I assume it has something to do with modprobe (.conf,.d,etc.), or am I barking up the wrong tree :)

---

### Post by carllfo on 2006-08-17
Bump

Please help if you can, this is the only thing that isn't working so far.  I do not want to go back to windows :sad:

---

