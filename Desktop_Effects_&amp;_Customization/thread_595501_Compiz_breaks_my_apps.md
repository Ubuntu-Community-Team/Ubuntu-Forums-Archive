---
title: "Compiz breaks my apps"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by qbox on 2007-10-28
Hi all

When I start compiz and I try to play movie or to open azureus for example, the program run and close emidiatly. I ask this question to another place and they send me here.
I run VLC from console:

qbox@qbox:~$ sudo -i
root@qbox:~# vlc
VLC media player 0.8.6c Janus
starting VLC root wrapper... using UID 1000 (qbox)
[00000308] ts demuxer error: cannot peek
X Error of failed request: BadAlloc (insufficient resources for operation)
Major opcode of failed request: 140 (XVideo)
Minor opcode of failed request: 19 ()
Serial number of failed request: 83
Current serial number in output stream: 84
root@qbox:~#

When I turn off compiz or desctop effects its work fine.
Thank you

---

### Post by daengbo on 2007-10-29
Some applications don't work well with 3D effects. It's safest just to turn them off when using one of these programs.

You can try going into VLC and changing the overlay method from XV to X11. That will probably help, but I can't be sure.

I know that Totem works quite well with the effects on.

---

### Post by qbox on 2007-10-29
> **daengbo said:**
> Some applications don't work well with 3D effects. It's safest just to turn them off when using one of these programs.

You can try going into VLC and changing the overlay method from XV to X11. That will probably help, but I can't be sure.

I know that Totem works quite well with the effects on.

Can you tell me exactly where to make this change? I mean what file.

---

### Post by Vivek788 on 2007-10-29
but then compiz fusion is enabled by default..my d4x and azureus crashes saying core dump abort...so do i disable and enable fx everytime i choose to use these?

---

### Post by qbox on 2007-10-29
I must disable desktop effects if I want to watch a movie or to use azureus. Any fix for this bug?

---

### Post by daengbo on 2007-10-29
qbox,

I'm not going to give you good news. I don't know VLC well, so I can't tell you exactly where to change the overlay characteristics. It should be in the video section. That change may or may not work. Azureus is a Java program, and I'm not sure how it interacts with the graphical display, so I can't tell you whether any changes there would help. Are you using the version for Sun's JRE or Gnu's JRE?

Really, you'll be better off using applications which are well supported under Ubuntu (and therefore Compiz). These would be Totem for playing movies and Deluge-torrent for torrents.

There's a reason VLC and Azureus are in the Universe section, They are unsupported.

To make sure all the codecs are installed, click [here]("apt:ubuntu-restricted-extras") and test Totem with your files. It works well with Compiz. If you need to play some WMP files, you'll need to install w32codecs (I leave that to you).

---

### Post by qbox on 2007-10-30
Thanks. Now I try with totem and he didnt close in. But I cant see picture. I try to install drivers and nothing.

---

### Post by daengbo on 2007-11-01
What kind of video is it? What's the codec?

---

### Post by qbox on 2007-11-01
I cant play nothing, avi, mpeg etc
VLC dont need a codecs and can play all video files...

---

### Post by daengbo on 2007-11-02
You used Totem and didn't see a picture, right? Are you using Ubuntu 7.04 or 7.10?

For Totem, try running Gstreamer properties by hitting ALT-F2 and typing gstreamer-properties at the prompt. The properties window should open. Go to the video tab and change the default driver to X11 (no XV). Close and try to play the video again. Tell me if that works.

---

### Post by bach on 2007-11-04
I am having exactly the same problem running Gutsy on a DELL D630 notebook. The problem only happens when I activate the compiz visual effects. Changing the default driver to X11 (no XV) did not help. Hints are welcome.

---

