---
title: "Funny sound in ZSNES"
date: 2005-07-06
forum: Gaming &amp; Leisure
---

### Post by drummer on 2005-07-06
Hi,

I'm having problems with sound in ZSNES. I've done everything here: [http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753) but the sound is often 'spluttery' and a bit broken at times. I don't seem to have problems with sound in other applications and zsnes doesn't give me any errors either.

Any help would be appreciated as it can get quite annoying while I'm playing.

Many Thanks, drummer.

---

### Post by Shinitenshi on 2005-07-07
Well am a nub at this but this i what i did to get it working

[http://ubuntuforums.org/showthread.php?t=7488](http://ubuntuforums.org/showthread.php?t=7488)

Hope that helps :)

---

### Post by drummer on 2005-07-07
[QUOTE=Shinitenshi]Well am a nub at this but this i what i did to get it working

[http://ubuntuforums.org/showthread.php?t=7488](http://ubuntuforums.org/showthread.php?t=7488)

Hope that helps :)[/QUOTE]
 Thanks for the reply, but none of that worked.. I have the libsdl-debian1.2-alsa package installed (and it was the same with esd). running as root didn't do anything either :(

---

### Post by BoyOfDestiny on 2005-07-07
try sudo killall esd

Yes I hate esd and love zsnes, I've been using it for several years. If that doesn't work... I recall having some trouble intially, so I built the CVS version... but at that time I had just disabled esd... So not sure if there is a correlation. 

Also try installing the libsdl debian all, see if that helps =) 

Anyway good luck,

P.S (from memory) if you want to disable ESD by default, System->Preferences->Sound and uncheck start sound server.

---

### Post by jkndrkn on 2005-08-06
Having the same problem. Music in rom games was sample-based. A string, for example, consisted of a very short and looped bit. In my case, it is these kinds of sounds that sound choppy. What should be a simple smooth string or flute sound is a continuous splutter of samples. One-shot things like sword strikes and explosions that don't loop sound fine though.

I've tried every combination of sound configurations in zsnes.

I use the alsa mixer howto that is floating around in the forum and in the ubuntu wiki. I also use polypaudio to give me access to sound in games.

Anyone seen this problem?

---

### Post by BoyOfDestiny on 2005-08-06
Hi, I'm wondering what version you are running? 
1.36 is ancient, and 1.41 had a bug so they released 1.42. 

I currently run the CVS version ([http://sourceforge.net/cvs/?group_id=19677](http://sourceforge.net/cvs/?group_id=19677)) and the WIP's ([http://ipherswipsite.com/zsnes/)](http://ipherswipsite.com/zsnes/)). There are no linux binaries on that page, so you'd have to build it yourself. 

The only thing is you'd have to delete your zsnes config file I think (they fixed a "bug" that no longer requires this when u go from latest to latest)

Anyway if you get the source from the wips page, remember to do a chmod u+x on the autogen.sh

make sure you have build-essential, automake, autoconf, sdldev, etc etc

just type sudo ./autogen.sh
then make

if you get any errors about something missing, just grab it from it synaptic.

Good luck, hopefully the sound problem is gone in one of the new versions (I remember having a similar problem when I used what was in the repositories) :)

---

### Post by jkndrkn on 2005-08-06
I upgraded to 1.42, and still have the same problems. I imagine it has something to do with my sound configuration (alsa and polypaudio). Thanks anyway for the tip.

---

### Post by drummer on 2005-08-06
[QUOTE=jkndrkn]I upgraded to 1.42, and still have the same problems. I imagine it has something to do with my sound configuration (alsa and polypaudio). Thanks anyway for the tip.[/QUOTE]
 My problem (exactly as you described above, choppyness in loops) was fixed by changing the video size to a bit larger and to openGL rendering (config > video -- choose a size with 'O' in the parameters, I use '512x448     ODR   WIN'), rather than without (uses SDL then I think).

---

### Post by jkndrkn on 2005-08-07
Thanks for the suggestion. I tried it with no results. I then tried messing around with polypaudio and alsa and have lost all sound in zsnes. Sigh.

Odd. I followed the directions for configuring my alsa mixer. I have two soundcards installed and I use the second (hw:1,0). I installed polypaudio per recommendations of other users, and that seems to have given me (choppy) sound. I fooled around with apt-get, removing and reinstalling sdl and polypaudio stuff, and now my zsnes sound is gone.

When zsnes starts up, I have no error messages. It just simply seems like the alsa mixer is not working properly, and sound from zsnes (and other games) is not making it through..

Anybody have any ideas?

---

### Post by jkndrkn on 2005-08-08
No sound in videogames. Still. What steps have other users taken to let sound through?

I am using the alsa mixer and polypaudio as a replacement for esd.

Could this be an sdl issue?

Thanks

---

### Post by BoyOfDestiny on 2005-09-04
I think I might have stumbled upon a solution. 

I'm running breezy though... but anyway I have an x300 radeon mobility in my dell 6000... 

I had changed the xorg.conf to "radeon" instead of "ati"... In hopes to solve the tearing I get... (which seems to be normal for xorg, and will one day go away =) )

Anyway, when I ran zsnes... the sound was very staticky... when I set the driver back to "ati" and rebooted, sound was perfect...

Let me know if this worked/helped?

---

### Post by jkndrkn on 2005-09-04
Actually, while trying to fix the sound issue in zsnes I killed *all*  sound except that from xmms and haven't been able to recover it.

---

### Post by BoyOfDestiny on 2005-09-04
wow... I'd suggest to do a fresh install (or try breezy if you are feeling adventurous)

I don't know if you partitioned your drive, but if you decide to reinstall, put /home on another partition.

This came in very handy, and kept all my settings (and not having to copy all those roms over again... ;))

---

