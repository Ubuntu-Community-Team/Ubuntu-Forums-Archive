---
title: "Doom 3 problem"
date: 2005-08-28
forum: Gaming &amp; Leisure
---

### Post by WMCoolmon on 2005-08-28
Sound in Doom 3 is staticy, because it's sampled at 44100 hz. (I use an Audigy 2 NX, that ALSA doesn't fully support, unless (supposedly) you upgrade to 1.0.9...and I've never been able to get a working kernel to compile in Ubuntu, there are something like four different sets of instructions and apparently I have to do _something_ with packaging)

My /etc/asound.conf:
```
pcm.usb {
	type hw;
	device 0;
	card 0;
}

pcm_slave.sl {
	pcm usb
	rate 96000
}

pcm.!default {
	type plug
	slave sl
}

pcm.nx {
        type plug
        slave {
                pcm "hw:0,0"
                rate 96000
        }
}
```

Apparently the first three main items don't resample it, as the only thing I've been able to use to get it working is by setting programs to use the fourth main item. I believe it would be possible to use the "+set s_alsa_pcm" arg for Doom 3 to do it as well.

But, Doom 3 gives me this:
```
------------------------------------
dlopen(libasound.so.2)
dlopen(libasound.so.2: cannot open shared object file: No such file or directory) failed:\uffffU
H\uffffU
@n\uffff

Alsa is not available
----------- Alsa Shutdown ------------
```

Libasound is definitely installed at /usr/lib/asound.so.2; I've tried putting a symlink in the doom 3 directory, but it didn't make any difference.

Is there some way to fix this, ie make OSS automatically use the 'nx' device?

---

