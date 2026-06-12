---
title: "Desktop Environment for Intrepid Server"
date: 2009-03-30
forum: Desktop Environments
---

### Post by cfree220 on 2009-03-30
Hi,
I've been running a server headless for the past several months and have reached the point where I feel a GUI would be useful for certain tasks. When I was only using it for FTP and SSH file transfers and streaming, the CLI was fine. I'm now using it for hosting an audio streaming website. My music collection is quite large (about 10,000 songs). Many of the audio files are large-- there are plenty of .wav and .flac; the rest of the collection is, for the most part, .mp3 @256-320 kbs. MY school limits the amount of outgoing bandwidth, and streaming such large files eats this up quickly. Because of this, I need to be able to easily downsample my music and move around files and directories.

The server box is very old (almost ten years), and with only 256mg of total ram, cannot handle very much. I'd like the desktop environment to be very minimalistic and lightweight. Also, I do not want the machine to boot into graphical mode. Instead, I'd like to enter a graphical session with the startx command (it is my understanding that this sort of configuration will better use available resources).

Does anyone have any recommendations on how to go about doing this? I've heard it said that XFCE desktop environment is good for this... Does that have the potential to interfere with existing software (or does it only change the graphical frontend of things)? I've also heard that I can install just the x system core...

Finally, is there anything I would have to do to make sure it boots headless?

---

### Post by TenPlus1 on 2009-03-30
I personally use OpenBox as my window manager and have a full system in 60mb of memory, also IceWM is tiny and very light also...  Check this out for info:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by cfree220 on 2009-04-05
Thank you eleven,
I'm trying openbox on a VM before trying it on the server box to see how I like it. The link you provided was very helpful and informative and answered all of the questions in my initial post. I am a little confused as to how to naigate the GUI... there does not seem to be any toolbars or menus, apart from the configurable right click menu. I google image searched openbox window manager and noticed that they looked quite different from what i was looking at... I think this is because openbox is only a window manager, and not the desktop environment itself??? Just wondering if I need to install anything beyond xorg, or if there are any packages I can add that will improe usability without using up too many more resources...
Thanks again,
Chris

---

### Post by majamba on 2009-04-05
have to agree since Mark Shuttleworth seems always to compare ubuntu and osx. Comming from Mac OSX Server i feel that we need a gui.

---

