---
title: "SNES emus (both of them) not working..."
date: 2005-05-11
forum: Gaming &amp; Leisure
---

### Post by apu95 on 2005-05-11
Hey guys...I just started discovering the miracle of the synaptic package manager. Incredibly comfortable to have everything in one window :D

Anyways, I wanted to play DKC (I love that game XD) so I installed Snes9x at first. I installed the gtk frontend, snesexpress, and I tried running the game. It didn't run...it just stays there as if the game were actually running but no window is opened to show it. I don't know about that one...I tried using the OpenGL for it too and it didn't work, and the gnome frontend and it didn't work either.

Next I uninstalled snes9x and installed zsnes...this one worked a little better. I was able to get the game running, but alas, there wasn't any sound. I couldn't figure out why there wasn't any sound either, since the volume was turned way up (I could hear the Ubuntu sfx).

I'm not sure what other info I can post to diagnose my problem...

Any ideas?

Thx in advance,
Apu

---

### Post by gil-galad on 2005-05-11
I am guessing your laptop's sound card does not have hardware mixing in linux.  This is not normally a problem, because esd provides software mixing.  But when an application does not use esd there is no sound.

---

### Post by Sherack Nhar on 2005-05-11
One partial solution could be to run 
```
sudo killall esd
```
Just before running Zsnes.  It's because esd is hogging the /dev/dsp device, and zsnes needs it exclusively to output sound.  That's how I solved all of my no-sound issues in all my games.  It's not the best of solutions, but it works.  

When you're done playing, just run "esd" again to gain back your sound.

---

### Post by Stormy Eyes on 2005-05-12
While you're at it, I'd recommend fiddling with GNOME's settings to make it use ALSA directly. ALSA provides hardware mixing, and can be configured with dmix to provide software mixing without ESD.

---

### Post by Sherack Nhar on 2005-05-13
[QUOTE=Stormy Eyes]While you're at it, I'd recommend fiddling with GNOME's settings to make it use ALSA directly. ALSA provides hardware mixing, and can be configured with dmix to provide software mixing without ESD.[/QUOTE]
Do you have a good HOWTO to point out that deals with that?  I'd really like to know how to pull that off...

---

### Post by agds on 2005-05-14
[This thread](http://ubuntuforums.org/showthread.php?t=26567) may have the information you want.

---

### Post by Lupine on 2005-06-26
[QUOTE=apu95].... It didn't run...it just stays there as if the game were actually running but no window is opened to show it. I don't know about that one...I tried using the OpenGL for it too and it didn't work, and the gnome frontend and it didn't work either.....[/QUOTE]


I've come across this same issue.  It just sits there in the console, no errors but no game either.  Any one figure this out yet?  I can't seem to use zsnes either, as it seg faults upon launch.  I used to use snes9x all the time on my LFS laptop, and it worked fine....not sure what to do with this problem though. ](*,) 

Any suggestions?

---

### Post by Lupine on 2005-06-26
Bah nevermind.....I forgot I still have to "killall esd" even though I have it working with multiple sounds in Alsa.  weird.

---

### Post by RedMars on 2005-07-14
An alternative to killing esd ist to run your programs through esddsp (which is in some esd addon package): esddsp zsnes.

---

### Post by Seth on 2005-07-14
Here's a backported zSNES package, by me. It's got the newest available version of zSNES.

[http://sethkinast.com/ubuntu/hoary/backports/zsnes_1.420-0ubuntu1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/zsnes_1.420-0ubuntu1~5.04ubp1_i386.deb)

Currently installing libsdl1.2debian-all should fix your sound, if you use the backport.

---

