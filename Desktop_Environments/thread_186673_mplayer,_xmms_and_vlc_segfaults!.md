---
title: "mplayer, xmms and vlc segfaults!"
date: 2006-06-02
forum: Desktop Environments
---

### Post by nicco on 2006-06-02
I just updated to 6.06, and now none of my multimedia apps work! Mplayer, xmms and vlc segfaults immediately, I'm guessing it's a library that crashes. Has anyone else experienced this? Any clues on what I can do?

---

### Post by FredB on 2006-06-02
Erh... Did you try upgrading your xmms, vlc and Mplayer too ?

/me thinks it is a dumb question.

A more useful idea. Try to launch them from terminal, and tell us what errors you have.

---

### Post by nicco on 2006-06-02
Yep, I did. Strange thing is, I used mplayer after upgrading but before rebooting, and the new version worked fine (I saw the version number had changed etc.) But after booting it doesn't work.

The errors are as follows:
$ mplayer
Segmentation fault

$ vlc
VLC media player 0.8.4 Janus
Segmentation fault

$ xmms
Segmentation fault

All other programs work without problems :(

---

### Post by myrek on 2006-06-02
I had the same problem with 5.10 and

sudo touch /etc/ld.so.nohwcap

fixed it for me, but I have no idea why it works :D

---

### Post by nicco on 2006-06-02
[QUOTE=myrek]I had the same problem with 5.10 and

sudo touch /etc/ld.so.nohwcap

fixed it for me, but I have no idea why it works :D[/QUOTE]

Wow, that fixed it! Thanks a lot!

Googling for ld.so.nohwcap I found that this has something to do with how ld searches for libraries, but it really shouldn't crash either way. But I don't care, it works now :D

---

