---
title: "Problems with Jaunty and Amarok 2"
date: 2009-04-24
forum: Desktop Environments
---

### Post by terrrorr on 2009-04-24
FYI:

I got couple problems after I installed Amarok into my newly installed Jaunty.

Case 1. Scan Fails -> Empty collection
- Close Amarok
- Remove all files and directories from /home/[username]/.kde/share/app/amarok/
- Start Amarok and rescan your audio files

Notice: You may need to restart Amarok after rescan.

Case 2. Amarok skips all tracks in playlist
- Open your console
- Install libxine1-ffmpeg using apt-get (sudo apt-get instal libxine1-ffmpeg)
- Restart Amarok and try again

- Terrrorr

---

