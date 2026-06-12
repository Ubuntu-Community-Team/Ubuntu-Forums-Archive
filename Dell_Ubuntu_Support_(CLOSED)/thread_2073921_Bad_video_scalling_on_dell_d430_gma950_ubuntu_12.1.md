---
title: "Bad video scalling on dell d430 gma950 ubuntu 12.10"
date: 2012-10-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Uraiah on 2012-10-20
I've got a problem with my dell d430 with c2d u7600 and gma950. When i run any fullscreen app in any other resolution than my native resolution (which is 1280x800) then the video is incorrectly scalled - i see only ~1/4 of the video, it really annoys me, cause i can't play any game in low resolution (gma950 isn't too powerful so i can't play most games in native resolution), the problem occurs on any renderer - OpenGL, SDL or DirectX (via wine). the problem did not occur on Ubuntu 12.04 - everything was running fine until i upgraded to Ubuntu 12.10 (well, i didn't upgrade, i've made a clean install). What I can do to see correctly scalled games in resolution such as: 640x480, 800x600, 1024x768?
There are some links to photos of these problems:
Only 1/4 of video is visible on the screen:
[https://dl.dropbox.com/u/16115636/SAM_0383.JPG](https://dl.dropbox.com/u/16115636/SAM_0383.JPG)
After killing the process of blobby volley via bash:
[https://dl.dropbox.com/u/16115636/SAM_0385.JPG](https://dl.dropbox.com/u/16115636/SAM_0385.JPG)
On native resolution everything is fine:
[https://dl.dropbox.com/u/16115636/SAM_0386.JPG](https://dl.dropbox.com/u/16115636/SAM_0386.JPG)

---

### Post by dtg01100 on 2012-10-29
i have the same issue on my desktop and laptop, reported the bug at [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1072889](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1072889)

---

