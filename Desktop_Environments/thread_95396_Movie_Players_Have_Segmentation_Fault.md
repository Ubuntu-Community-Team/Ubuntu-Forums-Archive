---
title: "Movie Players Have Segmentation Fault"
date: 2005-11-26
forum: Desktop Environments
---

### Post by jacksonyee on 2005-11-26
Dear fellow breezy users,

My media players were working fine in Hoary, but ever since I have upgraded to Breezy, neither mplayer, gxine, nor vlc will work without giving me a segmentation fault.  The gstreamer-based players work just fine, but unfortunately, I need a libavcodec player in order to play my old videos which I encoded with mencoder.  

The strange thing is that on my laptop, everything works just fine - and that was installed using the exact same packages which I downloaded using apt-get -d and then copied over to this computer.  

I would appreciate it if anyone else had any ideas.  I have already installed and reinstalled the faulty applications without any success, and everything else on the system besides the Nvidia drivers work without any problems (the Nvidia drivers give me a blank screen and totally kills the system if I try to use them instead of the nv driver).

---

### Post by jacksonyee on 2005-11-26
Well, it seems that I have resolved the problem in a manner of speaking.  I copied my entire /usr directory from the other computer to the laptop, and now no more segmentation errors occur.  There must have been some corrupted library which gxine, mplayer, and wxvlc share which was causing all of those programs to crash.

It seems rather strange that this would occur since I thought that all .deb's had checksums, but in any case, I'm glad that this fix worked.

---

