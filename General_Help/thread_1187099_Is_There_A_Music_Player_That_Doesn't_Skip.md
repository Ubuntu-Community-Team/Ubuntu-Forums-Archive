---
title: "Is There A Music Player That Doesn't Skip?"
date: 2009-06-14
forum: General Help
---

### Post by pemur1 on 2009-06-14
After adding songs to my MP3 player, I went to check to make sure everything sounded OK. When I played the songs on Rhythmbox, Exhaile, and Amarok, a majority of the songs skipped in various locations. I checked them in Microsoft Media Player (ugh), and none of the songs skipped. Is there a media player available in Linux that doesn't skip? Or am I just being too much of a perfectionist? Thanks for any assistance.

---

### Post by sigixv on 2009-06-14
could it be that you have a slow pc? this only happens to me if i'm running a huge number of programs...

---

### Post by Chrus on 2009-06-14
Ive been using songbird and have had no trouble with it. Give it a shot and see how it goes.

[http://getsongbird.com/]("http://getsongbird.com/")

---

### Post by nandemonai on 2009-06-14
Sounds more like a sound driver issue than any particular software.

All the listed players work fine here, even in virtual machines ;)

---

### Post by pemur1 on 2009-06-14
> **sigixv said:**
> could it be that you have a slow pc? this only happens to me if i'm running a huge number of programs...

I don't think so. Even if I'm running only the music player, the songs still skip.

---

### Post by pemur1 on 2009-06-14
> **Chrus said:**
> Ive been using songbird and have had no trouble with it. Give it a shot and see how it goes.

[http://getsongbird.com/]("http://getsongbird.com/")

I'll give that a shot. Thanks.

---

### Post by sigixv on 2009-06-14
better to use this link then for songbird

[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

---

### Post by AICollector on 2009-06-14
I had the same problem with Exhaile, Banshee did the trick for me (Songbird is just a bit too unreponsive for me, but I like it anyway)

---

### Post by james_xxx on 2009-06-26
Pemur1, I would be curious to know what kind of machine you are using, and what kind of audio adapter.

I am having the same problem when playing mp3's (perhaps other audio, as well) using a Dell Mini 9 (Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)).

For me, this problem did not surface until some time in the last few weeks. Prior to that, I'd had no issues at all.

---

### Post by siryuhan on 2009-06-26
You could also try mplayer.

sudo apt-get install mplayer

mplayer /directory/to/mp3/files/*.mp3

---

### Post by james_xxx on 2009-06-26
Skipping takes place with mplayer, as it does with any other player.

Just to experiment, I just tried installing a few other players that do not use gstreamer to see how well they might do. I tried xfmedia and even banshee. Neither of them would play mp3's at all, to my very great surprise.

I have all the codecs, etc. installed, and as I mentioned earlier, up until a few weeks ago, I had no issues with audio on this Mini 9 at all.

---

### Post by 3Miro on 2009-06-26
It is a driver issue, however, I don't know enough to help. Try reading on the sound servers (google how to and so on).

---

### Post by Th3_uN1Qu3 on 2009-06-26
It is not necessarily a driver issue. Get rid of pulseaudio. It's the worst thing ever.

```
sudo apt-get remove pulseaudio
sudo apt-get remove alsa
sudo apt-get install alsa
```

Then go into Sound Preferences and set everything to ALSA. Done.

---

### Post by philcamlin on 2009-06-26
quit some programs

---

### Post by Slim Odds on 2009-06-26
> **Th3_uN1Qu3 said:**
> It is not necessarily a driver issue. Get rid of pulseaudio. It's the worst thing ever.

I totally disagree. I know that some people have issues with it, but it works absolutely fantastic for me.

It probably depends on what audio hardware you have. But I get audio mixed from all my applications (including WINE).

The OP's problem is likely hardware related or the audio driver for their specific hardware.

My audio never skips, even when running all 4 cores to the max.

---

### Post by cmost on 2009-06-26
If you're playing the mp3 files from a USB drive, then you should be aware that a bug in Ubuntu causes USB 2.0 devices to run at USB 1.0 speeds in some cases.  There are numerous bug reports on this and apparently the bug has existed since Ibex.  I had this problem with the stock kernel and the new 2.6.30 kernel and went back to the 2.6.29.5 kernel to solve it.  If installing a new kernel is out of your league, then as a band-aide measure, you could use Audacious and define a large buffer.  Do this as follows:

1.  Launch Audacious
2.  left-click the small square in the upper left-hand corner of the player window
3.  Select preferences; then the audio icon on the left of the resulting window
4.  Change the Buffer size to something like 1000 (play with it until the skipping stops.)

Good luck!

---

### Post by 3Miro on 2009-06-26
Pulse has always worked for me, I am now happy to be back to it after some bad experience with Kubuntu's sound. I get good sound using wine + virtual box + Audacious at the same time.

If the Linus system is set up properly, sound doesn't skip, that is why I said that it must be a driver/setting issue.

---

### Post by james_xxx on 2009-06-26
I wound up following Th3_uN1Qu3's advice, and removing pulseaudio. 

I am not sure why I didn't decide to do this earlier, considering that I have been trying to correct this problem for several hours now, and had already had a very long and dysfunctional relationship with pulseaudio.

This appears to have solved all of my audio issues.

---

### Post by Student Driver on 2009-07-24
I am having similar issues with my Dell Mini 9, with nothing else running.  I will give this a shot (and it didn't skip with Vista or Windows 7 on it, so the hardware and CPU are fine).

---

### Post by Student Driver on 2009-07-24
I guess it's time to investigate PulseAudio, because my sound works perfectly fine now.  I was used to OSS, and later ALSA, but being away from Linux has made me miss a few "new" things and this is one of them.

---

