---
title: "Time taken to burn audio CDs"
date: 2005-10-20
forum: Desktop Environments
---

### Post by petehall on 2005-10-20
Something has been niggling me for a while - how come Nero on Windows can burn an audio CD in about two minutes, whereas using gnomebaker takes about five times that just to convert MP3 to CDDA? Is Nero cheating somehow?

I haven't tried Serpentine - is it faster?

---

### Post by Dolphin on 2005-10-20
I personally found gnomebaker to be bloody awful, despite what some people have had to say about it.

k3b is supposed to work well, but I generally usually use NeroLINUX.  Mind you, NeroLINUX isn't free.

Be sure you have DMA enabled for your writer as well.

---

### Post by objorkum on 2005-10-20
Tried "graveman" ? Great program that fits into GNOME (K3b requires KDE...)

---

### Post by Dolphin on 2005-10-20
[QUOTE=objorkum](K3b requires KDE...)[/QUOTE]

You sure?  That doesn't sound right to me.

---

### Post by petehall on 2005-10-20
[QUOTE=Dolphin]Be sure you have DMA enabled for your writer as well.[/QUOTE]

I do, but the really really slow stage seems to be converting MP3 to CDDA, which is a process that takes place prior to burning. How can Nero perform this conversion so much more quickly than gnomebaker? Does Nero for Linux do it as quickly?

---

### Post by petehall on 2005-10-24
Update: I tried Serpentine the other night, and it is much faster than gnomebaker for audio CDs - the process was pleasingly quick. It's not a completely rigid test, as I have recently updated my processor from an Athlon 1100+ to a Sempron 3000+. In fact, it's a pretty lousy attempt at a controlled experiment. But my mind is set at rest that Serpentine is probably as fast as Nero, and I may try burning an audio CD with gnomebaker to see how much of this improvement is down to the CPU speed.

---

### Post by zyrixnet on 2005-10-24
Hello,

    Have you heard of this console program called 'mp3burn'? It's new version is now able to burn m3u playlists from applications such as XMMS. It's pretty quick, since it doesn't need to update any progress bars, or anything for that matter. I find that applications that use less GUI components, or even none, seem to run more quickly.

    Plus, what I believe this 'cheat' that Nero does, that you are refering to, is what's called 'Burn on the fly'. It pipes the sound converter with an application such as 'cdrecord' or 'cdrdao'. mp3burn uses piping to burn playlists on the fly. It should be very simple to create a front-end for mp3burn. Simply use zenity to ask the user for a m3u file to burn, then open a console, and display the results.

    Hope some of this information was helpful.

---

### Post by missmoondog on 2006-02-07
i've searched for this topic a few times before. never found this thread. i was just searching for "sound convertor" when i found it. i've noticed the same thing also. fastest i can safely burn on any of my 6 systems is 12x. can burn at the max under windows xp pro on all machines. i think linux cheats some also at telling you the speed it's doing anything at. for only burning at a 12x, it only takes about 3-4 minutes to do a complete 80min cd-r on any of my ubuntu boxes, whereas burning at 52x in windows, takes 2-3mins.

---

### Post by groovywombat on 2006-02-08
I have to say, serpentine doens't seem much faster, takes forever to convert those files.  As far as actually burning goes, doesnt seem to be much of a problem.  but none the less takes too long to convert that shiiit

---

### Post by Sherwood Shark on 2006-02-08
I've given up on converting from shn or flac to wave in Ubuntu - it's just too slow!  Maybe it's my machine (PIII 800, 384mb ram) but I don't think so.  Now I burn stuff in the format I get it and move it to my XP box to convert to wave.  mkw and flacfrontend fly compared to sound converter (and it's the fastest I've found).

I do like kb3.  It works great for burning data files and wave files.  It's by far the best I've found so far.  

It's going from shn and flac to wave that's stopping me from doing it all in one place.

SS

---

