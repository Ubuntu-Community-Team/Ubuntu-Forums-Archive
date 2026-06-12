---
title: "Help, please"
date: 2005-03-08
forum: Desktop Environments
---

### Post by eraos on 2005-03-08
I'm not sure where this belongs since I think it has more to do with the OS itself than with my sound card.

First, I'd like to make a defensive statement: I am almost completely new to linux.

Anyway,
I d/led the alsa driver package and I tried to configure it:

```
root@Ubuntu:/home/nick/alsa-driver-1.0.8 # ./configure --with-cards=ice1712 --with-sequencer=yes;make;make install
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
make all-deps
make[1]: Entering directory `/home/nick/alsa-driver-1.0.8'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/nick/alsa-driver-1.0.8'

Please, run the configure script as first...

rm -f /snd*.*o /persist.o /isapnp.o
make[1]: Entering directory `/home/nick/alsa-driver-1.0.8/acore'
Makefile:6: /home/nick/alsa-driver-1.0.8/Makefile.conf: No such file or director y
make[1]: *** No rule to make target `/home/nick/alsa-driver-1.0.8/Makefile.conf' .  Stop.
make[1]: Leaving directory `/home/nick/alsa-driver-1.0.8/acore'
make: *** [install-modules] Error 1
root@Ubuntu:/home/nick/alsa-driver-1.0.8 #
```

Can someone help me with what this means?

---

### Post by bored2k on 2005-03-08
First of all are you getting no sound at all from ubuntu ? [u didnt specify if u just wanted alsa or what] From -any- sound architecture? ESD/Arts/OSD ??

---

### Post by eraos on 2005-03-08
[QUOTE=bored2k]First of all are you getting no sound at all from ubuntu ? [u didnt specify if u just wanted alsa or what] From -any- sound architecture? ESD/Arts/OSD ??[/QUOTE]

I'm getting "boops" if I click on system stuff.  But, as far as I know, I'm not getting anything else.  I apparently don't have an mp3 codec to test out mp3s.

Yeah, I wanted to install alsa becaues I thought it would work.  I was unsuccessful with both OSS and alsa on FC3.

I just installed the gcc thing and I get a step further in the configuration process until it hits something about "all deps"

```
checking for which soundcards to compile driver for... configure: error: Unsupported soundcard ice1712
make all-deps
make[1]: Entering directory `/home/nick/alsa-driver-1.0.8'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/nick/alsa-driver-1.0.8'

```

---

### Post by eraos on 2005-03-08
I guess I am getting sound.  I'm hear stuff from Gaim through my speakers.


Whoa.  neat, eh?

But I popped in a cd this morning and nothing came out.  And, as I said, I guess I don't have an mp3 codec to test anything else.

---

### Post by bored2k on 2005-03-08
If ur getting the "boop" sound that means ur getting sound, wich is good.

Try this method and tell me if you get anything out of it :

1st of all, for mp3 playback, download gstreamer0.8-mad, xmms, and libmikmod -for more playback, also install gstreamer0.8-plugins.

How to install anything ? on ur panel hit Computer > Sys Config > Package Manager [synaptic], put ur passwd, and then clic reload to get updated sources.

And look them up theree.

---

### Post by bored2k on 2005-03-08
1. MP3 Playback installs:
gstreamer0.8-mad
gstreamer0.8-plugins
beep-media-player
libmikmod


2. If you're not getting multiple sounds at once, try this method [pointed to me by kassetra btw]
> 
Preferably for AC97 Sound -still should work on anything else

1. Install alsa-oss
2. Install alsa-headers
3. Make sure you have libesd0 and gstreamer0.8-esd installed. (if not, install)
4. Make sure esound and esound-common are installed. (if not, install)
5. alsa-base
6. alsa-utils
7. gstreamer0.8-alsa
8. libpt-plugins-alsa

Ok, next.
1. Right click on the little volume control in your top panel and the
choose Open volume control.
2a. *IF* it opens, you should see two tabs, one for OSS and the other
for Alsa. Make sure nothing is muted.

We're going to switch you to a sound daemon that allows multiple sounds.
1. In gstreamer-properties [u get here by Alt+F2 and writing that here], change the Default Sink to output: ESD -
Enlightenment Sound Daemon (Why not alsa you ask? Because alsa makes
crackling noises with the ac97)
2. Change your Output plugin in XMMS to eSound output plugin. (You
also might want to think about using beep-media-player ; it's
essentially identical to xmms, uses same plugins and skins, only it's
made for gtk2 and it's much nicer.)
3. Enable your sound server startup.

That should do it :-D

---

### Post by eraos on 2005-03-08
[QUOTE=bored2k]

1st of all, for mp3 playback, download gstreamer0.8-mad, xmms, and libmikmod -for more playback, also install gstreamer0.8-plugins.

How to install anything ? on ur panel hit Computer > Sys Config > Package Manager [synaptic], put ur passwd, and then clic reload to get updated sources.

And look them up theree.[/QUOTE]

About an hour ago, based on one of the HOWTOs on this forum, I tried downloading the gstreamer0.8-mad thing.  apt didn't find it.  And in Synaptic, I don't see a -mad.  There are over a dozen gstreamer downloads, but none of them have -mad.

Thanks for the help so far.

---

### Post by bored2k on 2005-03-08
[QUOTE=eraos]About an hour ago, based on one of the HOWTOs on this forum, I tried downloading the gstreamer0.8-mad thing.  apt didn't find it.  And in Synaptic, I don't see a -mad.  There are over a dozen gstreamer downloads, but none of them have -mad.

Thanks for the help so far.[/QUOTE]
 In synaptic clic on Settings > Repositories , and check every single box there [saying YES everytime it says whatever], after that, clic reload again and try, they should appear know .

---

### Post by eraos on 2005-03-08
OKay, OKay, I did the enable "universe" thing in Synaptic.  Now I see it.

Let me try it all out and I'll tell you the results.

---

### Post by eraos on 2005-03-08
[QUOTE=bored2k]In synaptic clic on Settings > Repositories , and check every single box there [saying YES everytime it says whatever], after that, clic reload again and try, they should appear know .[/QUOTE]
 Just did that as you were typing that post, haha

---

### Post by bored2k on 2005-03-08
[QUOTE=eraos]Just did that as you were typing that post, haha[/QUOTE]
  :-P

---

### Post by eraos on 2005-03-08
Ah, okay, mp3's are coming out now.  Just that cd is still not playing.  But that's good enough for me.  

Thanks a lot for the help.  Much appreciated.

---

### Post by godsunderstudysdad on 2005-03-08
Just browsing he forums and came across this interesting thread. There is a similar one in the ppc section (cd player, cd ripper). Same problem. Quick recap on our experience:
Linux newbie. Installed Warty Gnome to run (almost) native under Mac OS X, installed Warty Ubuntu on a separate partition, upgraded it to Hoary Ubuntu and Hoary KUbubtu (love all of it except the name KUbuntu), apt-got everything recommended to solve the problem, [COLOR=Purple]but the cd will still not produce a sound[/COLOR]. I can see it playing, I can read track listings, I can burn it (slowly) then play it, I can eject it, but I can't plaay it.
The player and burner packages are not at fault, but whatever makes the cd player talk to the sound output. Least, thats what I think, but I have no idea what to do about it.

---

### Post by eraos on 2005-03-09
[QUOTE=godsunderstudysdad]but the cd will still not produce a sound[/COLOR]. I can see it playing, I can read track listings, I can burn it (slowly) then play it, I can eject it, but I can't plaay it.
[/QUOTE]

Yeah, that is my problem.  But also, when I go to the filesystem and click on the cdrom1 icon, I get an error message saying something about unable to mount the drive... and it lists a few possible reasons like it my be in the wrong format or something.

---

