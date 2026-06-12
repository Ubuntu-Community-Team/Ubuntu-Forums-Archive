---
title: "NWN - libSDL patching for fullwindow-toggle"
date: 2010-07-14
forum: Gaming &amp; Leisure
---

### Post by Struwelpeter on 2010-07-14
Hey there,

Being a non-native English speaker, I have to consult my dictionaries while playing RPGs, and therefore having Neverwinter Nights toggle between full screen and windowed mode is essential. I have been thus trying to install zzq's SDL/NWN FullScreen toggling patch ([http://home.roadrunner.com/~nwmovies/](http://home.roadrunner.com/~nwmovies/)), but I'm coming across an error. In case there's anybody out there familiar with this specific patch, or with patching in general, here's what is happening:

I run zzq's patch (patch -p1 < fullscreen-toggle-125.patch), and then I configure libSDL (./configure --enable-pulseaudio). No error messages up to then. But when I try to compile libSDL ("make"), I get the following errors:

c SDL_alsa_audio.c  -fPIC -DPIC -o .libs/SDL_alsa_audio.lo
SDL_alsa_audio.c: In function 'ALSA_OpenAudio':
SDL_alsa_audio.c:272: error: too few arguments to function 'snd_pcm_hw_params_get_channels'
SDL_alsa_audio.c:282: warning: passing argument 3 of 'snd_pcm_hw_params_set_rate_near' makes pointer from integer without a cast
/usr/include/alsa/pcm.h:622: note: expected 'unsigned int *' but argument is of type 'int'
SDL_alsa_audio.c:292: warning: passing argument 3 of 'snd_pcm_hw_params_set_period_size_near' makes pointer from integer without a cast
/usr/include/alsa/pcm.h:650: note: expected 'snd_pcm_uframes_t *' but argument is of type 'snd_pcm_uframes_t'
SDL_alsa_audio.c:294: warning: passing argument 3 of 'snd_pcm_hw_params_set_periods_near' makes pointer from integer without a cast
/usr/include/alsa/pcm.h:663: note: expected 'unsigned int *' but argument is of type 'int'
make[3]: *** [SDL_alsa_audio.lo] Error 1
make[3]: Leaving directory `/home/struwelpeter/nwn/SDL-1.2.5/SDL-1.2.5/src/audio/alsa'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/struwelpeter/nwn/SDL-1.2.5/SDL-1.2.5/src/audio'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/struwelpeter/nwn/SDL-1.2.5/SDL-1.2.5/src'
make: *** [all-recursive] Error 1

Any clues as to what the problem might be? I know this may be too specific but there's no harm in asking, I hope!

Cheers,

S.p.

---

