---
title: "[SOLVED] mocp problem?"
date: 2008-12-23
forum: General Help
---

### Post by abhilashm86 on 2008-12-23
i tried running mocp to play an audio,so it could'nt find drivers?
abhilash@abhilash-desktop:~$ mocp
Running the server...
Trying JACK...
Trying ALSA...
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Trying OSS...

FATAL_ERROR: No valid sound driver

FATAL_ERROR: Server exited

what should be done?

---

### Post by andrew.46 on 2008-12-25
Hi again abhilashm8!

Good to meet you again :-). With moc I am not on such sure ground as mutt but it certainly runs nicely on my system as the attached screenshot demonstrates. moc cycles through 3 sound drivers on startup and obviously had trouble with all of yours. To adjust these and other values manually you can copy a configuration file to $HOME as follows:

```
 zcat /usr/share/doc/moc/examples/config.example.gz > ~/.moc/config
```

and open with your favoured text editor. The relevant section is:

> # Sound driver - OSS, ALSA, JACK, or null (only for debugging)
# You can enter more than one driver separated by a coma. The first working
# driver will be used.
SoundDriver		= JACK, ALSA, OSS

But certainly on my system this required no intervention on my part and the program just worked :-). Have you compiled your own or is it from the Ubuntu repository? If you have compiled you need to ensure that the relevant -dev files are in place.

If problems continue there is [a moc forum]("http://moc.daper.net/forum") where the developers of the program help out.

All the best,

 Andrew

---

### Post by abhilashm86 on 2008-12-26
hey thanks andrew!!!!!!yea the servers were not predefined,so it was a problem,now i am able to run mocp,gud one:)

---

### Post by glotz on 2008-12-26
Also try mpd (+ mpc) + ncmpc. It's a wonderful combo.

---

