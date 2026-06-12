---
title: "SdlMame (v 0.141) Sound issues--Crackles Pops"
date: 2011-01-15
forum: Gaming &amp; Leisure
---

### Post by jukingeo on 2011-01-15
Hello all,

In the past I really didn't have much issues with running SdlMame in Ubuntu Studio Hardy (8.04).   But I recently bought a machine and naturally upgraded everything as I went along.  I changed my Ubuntu to Ubuntu Studio Lucid (10.04) and I changed my SdlMame to 0.141.  Now I am having a sound issue.  During the game I have noticed a crackling sound in the audio output.  Mind you this is happening with simple games such as Pac Man, Dig Dug, etc. I never had this before.  I tried a couple different driver options and I made sure I was using Pulseaudio and that didn't seem to work.

I am looking for suggestions as to what else to look for.

Thank You,

Geo

---

### Post by mocha on 2011-02-01
I'm not at my box right now, but to solve this you install a package "libsdl esd" with a name similar to that.  Then you set an environment variable SDL_AUDIODRIVER=esd in your .profile.  In the mame.ini you specify esd in the audiodriver line.  Then the problem should be solved.  This is documented numerous places, it's a really old issue.

---

### Post by jukingeo on 2011-02-05
> **mocha said:**
> I'm not at my box right now, but to solve this you install a package "libsdl esd" with a name similar to that.  Then you set an environment variable SDL_AUDIODRIVER=esd in your .profile.  In the mame.ini you specify esd in the audiodriver line.  Then the problem should be solved.  This is documented numerous places, it's a really old issue.

Hello Mocha,

I got as far as the mame.ini file and there I was stopped in my tracks as there is no "audiodriver" line.  Please advise further.

Thank You,

Geo

---

### Post by mocha on 2011-02-07
At the bottom of the mame.ini add this:

```
audiodriver               esd
```

The package I was talking about installing is called libsdl1.2debian-esd

In your ~/.profile and ~/.bashrc files add this at the bottom:

```
export SDL_AUDIODRIVER="esd"
```

Reboot for good measure, try again.

---

### Post by jukingeo on 2011-02-12
Hello Mocha

Ok, I tried that last bit out and rebooted.  The sound is a little bit better, but unfortunately I am still having the crackling issues.

By crackling I mean it sounds like a scuffed up record.  The sound does play, but with "crackles and pops".

Some games are worse than others.  For example with Asteroids, you barely hear the crackles and the sound is somewhat livable.  The Pac-Man / Galaga series, the pops are noticeable.  For Dig Dug, it is horrendous.  With Dig Dug, the sound sounds like it is tripping up on itself.

Now I do have a question with all these sound changes.  I do have SDLMame right now on an Ubuntu Studio setup.  I do hope that these settings are not going to affect that.  Ubuntu Studio uses Alsa with Jack.  Granted I have not set it up as of yet because this machine is new and Lucid is a new install on this machine.

However, since the problem has not been eradicated, I am looking forward to the next step.

Please advise.

Thank You,

Geo

---

