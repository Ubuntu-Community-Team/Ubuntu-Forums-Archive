---
title: "Sound problem with Sacred Gold (native port)"
date: 2009-10-21
forum: Gaming &amp; Leisure
---

### Post by Eddward on 2009-10-21
Hi all,

    I am very new to Ubuntu but I'm very experienced with Linux.  I'm
coming from Gentoo most recently though I have used debian long ago.
I'm having a problem with sound in the native port of Sacred by LGP
(among other things).  During the opening movies and the in game
movies I get a lot of crackly distortion, to the point that I can't
make out the sound.  Usually sound give out before the end of the
movie and I get silence.  (I've also seen the with the opening movies
in X2 but I have not tried to play X2.)  In game, I get crackling
mixed in with the in game atmospherics.  On rare occasion I've had
similar with World of Goo and Zaz.

    I've tried search for help with Sacred on Ubuntu specifically but
have had little luck.  In general I saw a lot of problem involving
games and pulseaudio.  LGP recommended using pasuspender & padsp,
neither of which helped.  They also recommended using an OSS kernel
module for ALSA but said I'd need to get distro specific directions
for doing that.  I was not able to find that for Ubuntu yet, but I did
find a page about aoss which also did not help.

    I have tried not to modify the system configuration.  I was hoping
I would be able to run a mainstream system without have to customize
it too much to avoid problems that customizations can cause.  It did
try changing default-fragment-size-msec from 10 to 5.  This seemed to
help a little but the problems still persist.

    Prior to my recent migration to Ubuntu I had never used
pulseaudio.  On my previous OSes I just used ALSA and my emu10k card.
I never had sound problems and was able to get good sound from
multiple apps in parallel no noticeable load.  I had read about dmix
but never set it up.  Given my previous good luck with plain ALSA I am
considering removing pulseaudio using the directions at
[http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)
but I'm worried that this might be going very far off the reservation
very fast.  All the docs I've found while trying to find a supported
way to remove pulseaudio, insist pulseaudio is better than ALSA.  None
of them have solved the problem.  Personally, I don't see how one can
add more layers to the sounds stack, increasing the times data crosses
address spaces and expect better performance.

    On a side note, I'm beginning to wonder if I chose the wrong
distro.  I chose Ubuntu with the plans of eventually going to Ubuntu
studio.  I haven't been able to do sequencing and recording since I
gave up Windows (and Digital Orchestrator Plus) back in 2000.  It
moved to Gentoo years ago hoping I could make a custom system for
recording.  I could never get the right configuration of realtime
drivers, jackd and other apps to get reliable low latency sound with
midi and digital playback and recording all together.  Prior to
investigating my problem is Sacred, I just assumed Ubuntu Studio (and
any serious recording distro) would come pre-configured to use just
jackd and have everything using that.

    Anyhow, just to recap, I'd like help getting Sacred working right.
I'm hoping that will also help with my other games.  If you want to
mention anything about Ubuntu & Ubuntu Studio, go ahead.  Feel free to
talk me down if I'm way off base.  Will Karmic will fix everything?
It's nice to be back on a debian based distribution, even if the world
has moved away from of my old friend dselect.  I am worried though
that I am going to have to make too many customizations just to get
something as basic games working.  And I'm worried that Ubuntu isn't
as friendly as other distributions to people who customize a great
deal.

Edd

PS: sorry if my post looks funny.  I wrote it in emacs.  Last might I was up late writing a post like this and by the time I finished proof reading and hit preview my session timed out and I lost the post.  This time I prepared it in advanced, but I didn't want to go have an un-linewrap it.

---

### Post by Eddward on 2009-10-23
Since I don't know if I've just shot myself in the foot some way I won't called this solved, but I think have sound working correctly.  I could play the videos at the beginning of Sacred and I could play the game with sound and graphics at max quality without the slightest sound issue.

I followed the directions at [http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/) to disable pulseaudio.  I skipped the steps for editing /etc/pulse/default.pa since it looked like it would enable dmix and I've never used that before and I don't want to start.  Also instead of

```
asoundconf set-default-card Intel
```I did

```
asoundconf set-default-card Live
```since that's what 'asoundconf list'' called my card.  Oh and I didn't go to the page with Intel specific directions.

---

