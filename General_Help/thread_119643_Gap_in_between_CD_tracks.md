---
title: "Gap in between CD tracks"
date: 2006-01-19
forum: General Help
---

### Post by eaglescout1984 on 2006-01-19
Okay, I've tried two CD player applications and gotten the same result. When I play a CD that goes from one song right into the next (like Dark Side of the Moon,) a gap is put in between the tracks. I've tried this with Sound Juicer and XMMS. What do I have to change so it will lead right into the next track?

---

### Post by StefanoCole on 2006-01-20
But when you play the CD with a home stereo do you have the (2 seconds?) gap? If yes it could be how the CD is burned. 
From Ubuntu you can try to play it with Totem and check if it behaves the same.

Stefano

---

### Post by eaglescout1984 on 2006-01-20
This is a factory CD, so there are no gaps. I just tried it with Totem and it's actually a much longer gap that the other two.

---

### Post by moephan on 2006-01-20
To properly burn a cd with no gaps between track, you need to burn the disc in Disc At Once mode. This is typically referred to as "DAO", as apposed to TAO, which is Track At Once mode. Even if you set the gaps to zero and then burn TAO, there will be a "click" between gaps.

I think the right program for this is called cdrdao (just search synaptic for "dao" and you should find it). cdrdao is a command line tool, but it seems fairly easy to use. You basically write a text file that says what files to burn, and also what the pre-gaps should be.

The most comprehensive overview of how to rip and burn cds is probably to be found on etree:
[http://www.etree.org/linux.html](http://www.etree.org/linux.html)

That link might have more info then you need though. You can finds tons of great free performances to download and burn from etree, all totally legit. Good luck.

Cheers, Rick

---

### Post by eaglescout1984 on 2006-01-21
Once again this is a FACTORY CD. It was manufacured by Capitol records. I need to know why the CD players insert a gap.

---

### Post by moephan on 2006-01-22
Now I understand. This is a typical problem with computer based media players on all platforms. They are not implemented to buffer in between tracks, so they always pause or click going from track to track.

---

### Post by Ale_Psycho on 2007-04-15
I'm having the same problem, can any one help?

I'm having gaps between tracks in any player with original album cds that mustn't have gaps.

I'm using Ubuntu 6.10 and tested the following player: XMMS, Amarok, Sound Juicer, Rhythmbox and Totem.

I tried to set the DMA option to the CD drive and it's okey, but still there is gap between tracks in original cds...

Please someone help!!!

---

### Post by ricardisimo on 2007-06-23
I'd love to know this as well, not only for factory CDs, but also for playlists. "Dark Side of the Moon" is an excellent example of a set of songs that definitely can do without the pause. I refuse to believe there's no way to play songs like this seamlessly. Thanks in advance.

---

### Post by CrispyFried on 2007-06-23
as far as I know all computers will do this, its just the way computers treat CDs. every computer, no matter what drive, no matter what OS or player, has done this with me. even some DVD players do this when playing CDs.

hopefully someone will tell me Im wrong as this annoyes me too. doing such a thing to *Dark Side of the Moon* is just plain **wrong**.

---

### Post by ricardisimo on 2007-06-26
Well, I suppose we can merge all of the songs, either with an audio editor like Audacity, or while burning with k3b. Seems like a waste of either drive space or a blank CD, but it can be done.

---

### Post by ricardisimo on 2007-07-18
Actually, this has Linux written all over it. I would recommend everyone sending a note to the folks at Audacious, Amarok, etc., asking them to work the problem out. It would be yet another step up from MS & Mac to offer folks. Audacious' bug reporter/feature request system appears to be down right now, unfortunately... we can all try back in a week or two.

---

### Post by Simon G Best on 2007-09-02
I must just rant at the apparent stupidity of current CD players (as in programs for playing CDs).  Or perhaps it's more specifically a stupidity with Ubuntu?

Not that long ago, gapless CDs (such as Pink Floyd's Dark Side of the Moon) played properly - no gaps.  But, more recently, CD players have started doing it wrong.  And it seems so, so needless.

On my previous PC, I had the CD drive connected to the sound card by a little cable.  This just seemed to be the normal, ordinary way of doing it, and had been for years.  This meant that CDs could be played without the stuff having to go through the system itself.  It just went straight from the CD drive to the sound card, and out to the speakers.  That had the bonus that no matter how busy the system got, CDs just carried on playing, and playing just fine.  And there were no rogue gaps.

But then, one day, I replaced RedHat 9 with Ubuntu 6.10.  To my annoyance, I found that Ubuntu's CD players generally seemed to play CDs by reading the data off the CDs, and sending it out to the sound card, via the system itself.  No longer was the audio signal taking the direct route from the drive to the sound card.  This, to me, seemed to be an obvious stupidity that had somehow crept in to almost all the different CD players.  Fortunately, XMMS still played CDs properly, so I just started using that for CD playing.

Now, on my nice new Dell Inspiron 530n with Ubuntu 7.04 preinstalled, I'm finding that even XMMS doesn't work.  I haven't looked inside the box, yet, but I suspect that Dell haven't connected the drive to whatever passes for a sound card in this system.

Anyway, the point is that the idea that some people have, that CD players on PCs have always inserted gaps, is simply wrong.  It used to be normal for PC CD players to play CDs properly, with no rogue gaps.  It's only recently, or perhaps just with Ubuntu (and related systems), that there's this stupidity.

:mad:

---

### Post by Krydahl on 2007-09-02
I posted this thread:

[http://ubuntuforums.org/showthread.php?t=520924](http://ubuntuforums.org/showthread.php?t=520924)

asking a similar question a little while back. Aqualung did solve the problem for CDs I'd ripped (I didn't try it with a factory CD) but I found that it had a whole set of other deficiencies so I'm still using Rhythmbox and putting up with the gaps.

I'm hoping benanzo was right when he said the new version will fix the problem.

---

### Post by vanadium on 2007-09-02
Gapless playback surprisingly does not seem to concern very much people. Gapless players are scarce, even more so under Linux. Only for this reason, I use XMMM with the crossfade plugin. The crossfade plugin among other features brings perfect gapless playback, including for mp3 files with lame tags. The same plugin is also available for the XMMS derivative (clone? fork?) audacious. Audacious is under active development, XMMS not anymore.

---

### Post by laidback on 2007-09-02
In Audacious you can set the pause between tracks, I have it at 0. This may not be exactly what you want but it would appear that it doesn't add an extra silent period between tracks beyond that which is on the original.

I've just played some John Digweed "Transition" with Audacious, it's continuous play despite being separate tracks, there is however a slight audible detection as it moves from 1 track to the next. I'm not entirely sure what is does on the original but I suspect that it's intended to be continuous (why isn't it one track then?) with no detection as it switches tracks...perhaps. 

Think that's the best I can do for you, give Audacious a try.

PS
I'd say it plays better in Amarok!! I have no crossfading and no gap set in Playback.

PPS
I cannot detect the switch between tracks in Amarok, definitely better that Audacious..music is continuous with constant beat.

---

### Post by vanadium on 2007-09-02
Both XMMS and Audacious should allow for perfect gapless playback with the crosfader plugin. Amarok indeed will do perfect gapless playback for wav, ogg, flac, but not for mp3. mp3 is a format that inherently does not support gapless. The lame developpers have implemented a trick to have gapless working for mp3 as well. It involves the use of tags that indicate where the audio starts and stops. Caveat is that the software player must recognise and use these tags. Fact is that few implement it. If you stick with ogg or flac, then Amarok will do the job well.

---

### Post by laidback on 2007-09-02
You won't believe this but there I am resting in bed reading old LXFs before going to sleep and what do I come across but an Article on Amarok and GAPLESS playback.
Well, according to LXF80 June 2006 page 20 what you need is....Xine which now comes with gapless playback. I'm using Xine in my Amarok.
It's also of note that in my post above I was playing mp3 tracks, not sure how that squares with the above from vanadium.

And so to bed .

---

### Post by lognok on 2007-10-03
Hey guys, for gapless playback use Rhythmbox, go to edit->preferences->playback and put a checkmark in "Use craoosfading backend(requires restart)" and set slider to 0.0.

Restart application and play your favorite tracks gapless, voila! :guitar:

Note: does not play gapless from cd-player, only from hd, so you're forced to rip your cd's for gapless playback then.


Take care

---

### Post by Krydahl on 2007-10-03
I'm using Rhythmbox 0.10.0. I don't have a "playback" option under preferences. I can't find any mention of crossfading in the help pages. :confused:

---

### Post by lognok on 2007-10-04
Hi Krydahl, sorry for not specifying my version of Rhythmbox which is version 0.11.2

It's running in Ubuntu 7.10 beta

---

### Post by Krydahl on 2007-10-04
OK thanks. I'll have to update.

---

