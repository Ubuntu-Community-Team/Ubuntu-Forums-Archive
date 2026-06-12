---
title: "Sound recorder problem"
date: 2009-03-15
forum: General Help
---

### Post by mike0020 on 2009-03-15
I'm trying to use Sound Recorder to record something, however when I press the record button, at the bottom of the program it's telling me that minutes have gone by when really only a few seconds have. When I try to stop the recording the program freezes for about 30 seconds and when I try to play back the recording I see the actual time of the recording, however I hear nothing (although that may be due to another problem with my microphone preferences). Can someone please help me?


**Edit:**
Nevermind, after a bit of searching I found a solution here: [https://bugs.launchpad.net/ubuntu/+bug/36852](https://bugs.launchpad.net/ubuntu/+bug/36852)

All I had to do was enter this command in Terminal and everything worked: gconftool -t string --set /system/gstreamer/0.10/default/audiosrc pulsesrc

---

