---
title: "How to play a DVD with Mplayer?"
date: 2005-06-30
forum: Desktop Environments
---

### Post by lorenzo on 2005-06-30
Ciao,
If I insert a DVD in my ubuntu, Totem is automatically launched and the movie begins. What I now need is to play the same DVD with mplayer (I have an ati card and I use atitvout to watch movies on tv, but it works with mplayer only).

I see my DVD under /media/cdrom/

How do I play  it with mplayer?

I see there's a command >mplayer dvd://

but what exactly do I have to write after the //??

Can anyone help me?

Many thanks,
Lorenzo

---

### Post by manicka on 2005-06-30
[QUOTE=lorenzo]Ciao,

but what exactly do I have to write after the //??
Lorenzo[/QUOTE]

nothing, if this command doesn't work try mplayer dvd:/

---

### Post by lorenzo on 2005-06-30
well, this is what I get:

>mplayer dvd://

...
Playing dvd://.
Unable to open URL: dvd://

>mplayer dvd:/

...
Playing dvd:/.
File not found: 'dvd:/'
Failed to open dvd:/

>mplayer -dvd

...
MPlayer was compiled without libdvdread support.


I have installed "mplayer-custom". On synaptic I can see there are "mplayer-386", "mplayer-k6". Should I change the installation?

Thanks,
Lorenzo

---

### Post by lorenzo on 2005-06-30
Well, a little step forward:

I have removed "mplayer-custom" and installed "mplayer-586" (I have a P4).

Now the command >mplayer dvd:// is recognized. 

So it works? Not really. I get another error message:

>Starting playback...
>
>MPlayer interrupted by signal 11 in module: decode_audio
>- MPlayer crashed by bad usage of CPU/FPU/RAM.
>  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
>  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
>- MPlayer crashed. This shouldn't happen.
>  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
>  gcc version. If you think it's MPlayer's fault, please read
>  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
>  won't help unless you provide this information when reporting a possible bug.
>alsa-uninit: pcm closed

Had anyone experienced the same problem in hoary?

Thanks,
Lorenzo

---

