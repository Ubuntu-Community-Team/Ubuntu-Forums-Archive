---
title: "[SOLVED] No sound in Wolfenstein: Enemy Territory"
date: 2008-11-16
forum: Gaming &amp; Leisure
---

### Post by Burneddi on 2008-11-16
I know this has been posted here hundreds of times, but after googling the solution for this for ages (with no notable results) I've decided to ask myself.

Ok, so on my another computer which I run Ubuntu Hardy on, and my brother usually plays on, I have ET installed. The problem is, that sometimes (most of the time) it doesn't have sound. The only fix so far that has actually fixed this is repeatedly rebooting the system without having speakers on, waiting a couple of minutes, running ET and turning speakers on. I have no idea why it fixes it, but it does. Sometimes.

Still, the problem is there. It takes ages to get the sounds back on which is really irritating.

So far I've tried the echo [stuff] etc things, putting the echo stuffs in rc.local file and having Exit 0 in the end, installing the et-sdl-sound thing and running thru it and countless of more minor or major fixes, including setting my sound quality to max and using s_initsound 0, which, I think is someones idea of a joke because it just makes the game not use sound at all no matter what is the situation.

Daresay none of those have helped me.

The specs of the computer are
- ATI Radeon 8500 video card
- AMD Athlon 1700+ 1,5GHz processor (If i got the name correct..)
- 256mb RAM
- AT something AC97 sound card (I think)

Which should run ET, and so it does. But the sounds only work part of the time.

When I run thru console, it gives no errors, runs fine, except it says "sound system is muted", but after a bit of googling I figured that it does it on everyone, even on those who have it working. And it says that "sound sytem is muted" thing even though the sounds work...

Ok, thanks in advance

---

### Post by Burneddi on 2008-11-17
Oh, and if it matters (I think it does), when I go to the Sound settings window and do the "test" thing when I have selected ALSA or OSS, neither of them play any sound. I figured that I should reinstall them both, but the question is, how? Help would be appreciated.

---

### Post by drarem on 2008-11-17
Check out playdeb (beta), I installed it on my 64-bit amd system and was able to install wolf-et. It had to recycle the X screen one time after the install, but after that, the latest wolf et works flawlessly with audio.

Again that's playdeb, and you can google it.

---

### Post by tromort on 2008-11-18
have you tried: 
```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
```? that always works for me. oh first rune sudo -i to become root, then run this command.

---

### Post by ShodanjoDM on 2008-11-18
Maybe it's related to pulse audio. How about this:

> RTCW / Enemy Territory / True Combat Elite / Quake 3

To use those games with PulseAudio as audio server, you will have to follow instructions from [http://nullkey.ath.cx/~stuff/et-sdl-sound/](http://nullkey.ath.cx/~stuff/et-sdl-sound/). Padsp doesn't work with them... No need to try it.

From: [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

Check the site, it has link for the patch to enable the sound with pulseaudio.

---

### Post by Burneddi on 2008-11-19
Thank you all for your replies --

It seems that I managed to fix this problem by simply updating to 8.10. Now the sounds have worked all of the times I've tried, so it was probably caused by some old sound system or something. No idea. But now it works, and that's the most important thing :)

Thanks again.

---

### Post by Johnsie on 2008-11-19
Awwww... I thought you guys were talking about the original wolfenstien :-(

---

