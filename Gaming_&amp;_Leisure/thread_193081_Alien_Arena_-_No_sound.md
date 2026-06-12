---
title: "Alien Arena - No sound"
date: 2006-06-09
forum: Gaming &amp; Leisure
---

### Post by Xarkam on 2006-06-09
Hello,
I'm download alienarena and installt it. By there is no sound.
Look this:
```

xarkam@HYKSOS:~$ sudo alienarena2006
using /home/xarkam/.codered/data1/ for writing
using /home/xarkam/.codered/arena/ for writing
execing default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
/dev/dsp: Broken pipe
Could not toggle.
--------- [Loading Renderer] ---------
ref_gl version: GL 0.01
Initializing OpenGL display
...setting fullscreen mode 8: 1280 1024
Using XFree86-VidModeExtension Version 2.2
GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 6600 GT/PCI/SSE2/3DNOW!
GL_VERSION: 2.0.2 NVIDIA 87.62
.........

======== CRX Initialized ========

recursive shutdown

``` 
How to ave sound on my /dev/dps ?

ps: alsa-oss is installed

My asound.conf
```

xarkam@HYKSOS:~$ cat /etc/asound.conf
# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 0
}

# Allow mixing of multiple output streams to this device
pcm.dmixer {
     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
          # rate 44100
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"

     bindings {
          0 0
          1 1
     }
}

# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).

pcm.!default {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

# OSS control for dsp0 (needed?...this might not be useful)
ctl.dsp0 {
     type plug
     slave.pcm "snd_card"
}

# OSS control for dsp0 (default old OSS is mixer0)
ctl.mixer0 {
     type plug
     slave.pcm "snd_card"
}

``` 
Cheer.

---

### Post by siriusnova on 2006-06-09
I had the same problem, in the alien arena folder there is a crx.sdl file or something like that, and a crx file

i got this from the Alien Arena forums..

do the following in the alien arena folder rename the current crx to crx.old and the sdl crx to replace it,

mv crx crx.old
mv crx.sdl (or whatever its called) crx

try it now, it worked for me

---

### Post by FredB on 2006-06-09
[QUOTE=siriusnova]I had the same problem, in the alien arena folder there is a crx.sdl file or something like that, and a crx file

i got this from the Alien Arena forums..

do the following in the alien arena folder rename the current crx to crx.old and the sdl crx to replace it,

mv crx crx.old
mv crx.sdl (or whatever its called) crx

try it now, it worked for me[/QUOTE]

Interesting. I was facing the same issue. Thanks for the info !

---

### Post by Xarkam on 2006-06-09
Thanx, that's run fine :)

---

### Post by sharperguy on 2006-06-13
Thank you!

I had the same problem too, now the game is so great.

---

### Post by BuffaloX on 2006-07-07
Thanx.

Just downloadet it, no sound, fix found here in 0.5 seconds. 
Much better with sound on.:p

---

### Post by isnellgrove on 2006-09-06
thanks it fixed my problem too!

---

### Post by Lord Illidan on 2006-09-07
Me too.. This game is great!!

One issue. though. Game music is quite crackly...is it supposed to be like that?

---

### Post by bigken on 2006-09-07
fixed it for me too but also have the crackly problem :-k

---

### Post by Doctoxic on 2006-10-14
fixed for me as well - thanks

but like ohters sound seems to be slightly crackly

Doc

---

### Post by dxdemetriou on 2007-04-24
The problem fixed
Just edit the ~/.codered/arena/config.cfg and change to: set s_khz "48"
It doesn't work with 22 or 44 on some sound cards
Every time you change something from options must be changed, because returns to 44
It worked for me :)

---

### Post by dxdemetriou on 2007-04-24
The 48 works for me well, I hope to be the solution for all. I don't know what khz works each sound card. Just try, and let me know

---

### Post by Pdennis on 2007-04-24
Thanks!

---

### Post by bubbalouie on 2007-04-25
Worked a treat, thanks :)

---

### Post by fakie_flip on 2007-05-16
How can I fix the sound in the new version of Alien Arena? I have AA2007. I don't have those flles, so I can't rename them. Here is what I have.

chris@ubuntu:~/MY GAMES/alienarena2007$ ls
AlienArena           arena         crx.i686        data1       README.txt
AlienArenaDedicated  botinfo       crx.sdl.i686    fce16.dll   source
AlienArenaSDL        crded.i686    crx.sdl.x86_64  fce32.dll   version.txt
alienarena.xpm       crded.x86_64  crx.x86_64      Galaxy.exe
chris@ubuntu:~/MY GAMES/alienarena2007$

---

### Post by X1R1 on 2009-11-30
I donwloaded following artificial inteligence guide, everything except sound, and I dont have that file, what should I do? I have lastest version (downloaded from SVN).

any help would be really appreciated.

regards

PS: guide is [HERE]("http://gwos.org/doku.php/guides:64bit:alien_arena")

---

