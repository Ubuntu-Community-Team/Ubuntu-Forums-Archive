---
title: "(K)Ubuntu 11.10 - No sound in Neverwinter Nights"
date: 2011-10-16
forum: Gaming &amp; Leisure
---

### Post by greyspammer on 2011-10-16
Greetings!

 Under Kubuntu 11.04, my NWN worked perfectly. Now I have a new installation (no upgrade) of 11.10 and NWN has no sound anymore. I kept the old, working NWN installation, so I doubt the problem's located there (since nothing has been changed). Other applications (both ALSA and OSS) work fine. As do other SDL games (tested sdl-ball and biniax2 as 64bit apps and Rune as 32bit app).

 I get no error messages in the terminal emulator (not even with SDL_DEBUG set). I just have no sound and in the advanced sound options in the game, the list of sound providers is empty.

 Here's what I've tried so far:
 
[LIST]
[*]Activate/deactivate PulseAudio
[*]Deinstall PulseAudio
[*]Set SDL_AUDIODRIVER in the nwn script to 'alsa' and 'dsp' (with export)
[*]Removed the './lib' from the LD_LIBRARY_PATH in the nwn script
[*]Switched between libsdl1.2debian-all and libsdl1.2debian-alsa and back
[*]Ran NWN without KDE/Gnome from a clean X-Session (only evilwm and one xterm)
[*]Made sure that the outputs of 'fuser /dev/snd/*' and 'fuser /dev/dsp' are empty
[*]Set/unset SDL_DSP_NOSELECT
[/LIST]
  Made strace log of nwn and checked for obvious problems. Due to large size (35 MB), I could only skim through it, of course. The only thing I noticed is that it never actually loads libasound.so. 'ldd', when used on the nwmain binary also shows no reference to libasound. But I'm not sure if that's how it's supposed to be. Perhaps someone with a working NWN can cross-check that for me.

  I googled a lot and think I've tried all the usual hints that are mentioned here and elsewhere. If I missed something, please point me to it. Other than that, I'm open for ideas.

  I am using the amd64 version of Kubuntu, kernel 3.0.4 (self compiled with OSS compatibility). Soundcard is Asus Xonar D2X. ia32-libs are installed.

  I'll attach a few shell snippets for further information (especially the outputs of 'ldd' and 'ldconfig -p' - though don't know how helpful they'll be).

---

### Post by greyspammer on 2011-10-17
A little update on my progress:

Adding /usr/lib32/alsa-lib to /etc/ld.so.conf also did not help.

However, after I took the time to set up a complete 32bit chroot environment (as described [here]("http://ubuntuforums.org/showthread.php?t=24575")), I could run NWN from within that chroot environment *with* sound.

So I conclude that the original problem must have something to do with the 32bit compatibility layer of the dynamic linker. Whatever that might be. :confused:

While I now have a workaround, I'd still like to fix the issue properly (without wasting about 1GB to a 'second' chroot Linux). So if anyone has any further suggestions...

---

### Post by imachine on 2013-03-11
For running it in 12.10 amd64, removing ./lib from nwn startup script fixed sound working for me. ia32-libs-multiarch and ia32-libs are installed.

So now it contains:

export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH

Thought this might help someone in a similar situation as me (installed NWN Diamond Edition Polish from existing windows install, runs 1.70 community patch no problems, 1.69 linux client :))

---

### Post by wildmanne39 on 2013-03-17
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

