---
title: "Unable to use AV/C transport in Kino with MiniDV camera"
date: 2005-11-17
forum: Desktop Environments
---

### Post by 23meg on 2005-11-17
I have successfully configured my MiniDV camera to capture video in Kino by putting the video1394 and raw1394 modules in my /etc/modules and setting the capture device as /dev/dv1394/1 . However, the AV/C transport controls don't work and I have to manually press play/stop on my camera to do the capture. In the preferences, the AV/C device selection box is empty and when I click it, nothing comes up.

Any help appreciated.

---

### Post by glantucan on 2005-11-27
I managed to make the AV/C controls work installing libpt-plugins-avc (if i'm right and it's this one which makes it work) Kino recognises my miniDV camera and shows it on the preferences IEEE1394 tab. But when I enable VTR control and press any button ("play", for example) I loose the control and no button work anymore until I press stop on the camera. The tape is played if I pressed "play" but I can't stop it, pause it, or any other operation.

Don't know what's wrong because the movie plays smoothly even though i'm whatching it remotely through NX.

Hope this helps, hope somebody can help any further

Cheers!

Glantucan

---

