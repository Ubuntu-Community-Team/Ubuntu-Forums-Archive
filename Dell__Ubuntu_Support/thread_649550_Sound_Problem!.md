---
title: "Sound Problem!"
date: 2007-12-25
forum: Dell  Ubuntu Support
---

### Post by orthodoc on 2007-12-25
I got a new Dell Inspiron 1420. Since Dell is not selling the 1420n in India I installed Gutsy Gibbon (Ubuntu i386). Everytthing was running fine. Until I decided to run a movie, that is. No sound. To my surprise no sound on playing music as well. I fired up various players including Amarok, totem, mplayer and vlc. None of them would work. In fact the music players would hang. I uninstalled all the players and the codecs as well. I had installed the codecs using automatix, so this time around I installed them using synaptic making sure I got the dependencies right. But still no sound.
Then I hit the Sound preferences dialog box. On the devices tab, the Sound Events tested fine. I could hear good. But on the Movies and Music option there was no sound playback. In fact the dialog would freeze on clicking ont he test button. Same issue with the Sound Playback option under Audio Conferencing. All of them had the Autodetect option selection by default. The Default Mixer Tracks was by HDA Intel (Alsa Mixer).

The "lspci | grep -i audio" was: Intel Corporation 82801H (ICH* FAmily) HD Audio Controller (rev 02)

What do I do do get back the sound playback??

---

### Post by orthodoc on 2007-12-25
This is such a major irritant! I am bumping the thread.

I am trying to submit a bug report in launchpad, but the server is taking a long time to respond. I wonder whats happening!

---

### Post by natehall on 2007-12-25
Try this link here: [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly)

---

### Post by orthodoc on 2007-12-26
Thanks natehall for responding.

I did follow the instructions but the system refuses to budge.

Anything else you would like me to try?

---

