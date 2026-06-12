---
title: "Banshee drop-outs during playback"
date: 2006-02-28
forum: Desktop Environments
---

### Post by rosslaird on 2006-02-28
Seemingly at random times (but at least once every couple of minutes) banshee stops playback for about one second, then resumes, then stops again for a second, then resumes. (The second pause does not always happen.)

I have no idea what's going on here. None of the other music players does this (rhythmbox, amarok, beep, etc.)

Ross

---

### Post by bites on 2006-02-28
I can confirm this.  It only happens sometimes, Banshee's been playing fine for a few hours now.  It might be coincidence, but I've only had this behaviour after importing songs..

---

### Post by rosslaird on 2006-02-28
I'm glad it's not just me.
I have noticed that sometimes, if I let banshee play for a while, the incidence of drop-outs goes down.

---

### Post by mostwanted on 2006-02-28
I can confirm the same thing. Too bad.

*cough* Amarok ftw, even though I'm a Gnome user >_>

---

### Post by naes on 2006-03-01
I can confirm this as well, at worst it even crashes at random times.
Even without Audioscrobbler plugin installed it happens, so that rules that out.
A neat program, but sweeter with visuals :)

Sean

---

### Post by elanthis on 2006-03-01
For those who are experiencing the skipping frequently: how much memory is Banshee using?

I wonder if it might be the GC kicking in.  It shouldn't be kicking in at all if the app isn't allocating memory, though, so it could also be a sign of a leak.

(Which yes, can happen even with Python/Perl/Java/C#, and with a GC; all you need to do is keep allocating data you're never going to use and leave a valid reference to it, i.e., in a list or something that you don't actually use.  Pretty common too when you bind a GC-language to a non-GC one like C.)

---

### Post by ShanghaiTeej on 2006-03-01
I know banshee is taking up a lot of processing power on my comp.  I'm also getting the random skips that are sometimes frequent, sometimes sparse.

---

### Post by Silwenae on 2006-03-02
I have a similar problem with the music cutting out.  Has anyone filed a bug report yet?

I was under the impression Banshee used Gstreamer 0.10 - however Banshee wouldn't work for me until I installed the bad and ugly plugins for Gstreamer 0.8.

---

### Post by Donza on 2006-04-14
I can confirm same problem. I have all the latest updates installed. These drop-outs seem to occur mainly just after you have started Banshee. After few songs I haven't noticed any drop-outs.

---

### Post by drobvice on 2006-05-12
Wanted to update this thread.  I ran this line as I was having the same problem:

```
$ mono --debug /usr/lib/banshee/banshee.exe
```

I think the dropouts are related to musicbrainz query.  When the query is over, it's pretty smooth but I still get random nonresponsiveness and have to force quit sometimes.

---

### Post by !nkubus on 2006-05-30
Same here it's skipping on basically every file


Amd athlon64 3800+ Dual core
1go Ram

it shouldn't skip on this kind of con fig lol

---

### Post by blue_thunder on 2006-06-01
I've got it going on too, and I can't think of anything to explain it. Sometimes it's more frequent than others...it's very strange.

---

### Post by Czak on 2006-06-04
I have the same problem. I noticed that when Banshee runs, there are moments of increased CPU usage (up to ~40% on my Athlon XP 1700, whereas it generally is ~5%). That's when the dropouts occur.

---

### Post by gamma on 2006-06-04
Yea I think this is due to an import and it's looking up album art and what not. LEaving it open for a while and then restarting seems to fix it..

---

### Post by stfriesen on 2006-06-05
Same problem here.  Drop outs are so bad and so frequent that I have had to remove banshee and use another player until there is a fix.

---

### Post by !nkubus on 2006-06-05
[QUOTE=stfriesen]Same problem here.  Drop outs are so bad and so frequent that I have had to remove banshee and use another player until there is a fix.[/QUOTE]


Finally I got use the the clunky user interface of Listen. At least it's realy usable but to much options on the main screen.

---

### Post by mnl88 on 2006-06-05
I've been having the same problems.  So, I just use Banshee to sync my iPod, and use good ol' Rhythmbox for my regular playing needs.

Then again, I also notice that after playing songs for a while, the problem goes away.

Banshee, while just playing a regular MP3, uses 58.7 Mb of RAM for me.  It also doesn't seem to tax my CPU very much.  The load hovers around 10% with Banshee, Firefox, and the System Monitor open.

---

### Post by mmcmonster on 2006-06-06
I have the same problem on my AMD Athlon XP 3200+ w/ 512MB ram on dapper.

The skips are pretty frequent (at least 15-20 while listening to "Tiny Dancer" by Elton John (192 kbps mp3)).

Unfortunately, rhythmbox crashes for me quite often and has trouble adding soungs to playlists. Often the songs just don't get added, without giving any indication of failure. :-(

And I never could figure out how amarok works. ;-) (I have to set up similar systems for my parents and my brother, so I need something simple, anyway)

Somewhat off topic: Rhythmbox was much more stable for me on breezy. :(

---

### Post by t0mc4t on 2006-06-06
Try to disable the "metadata searcher" plugin.

---

### Post by mmcmonster on 2006-06-06
[quote=t0mc4t]Try to disable the "metadata searcher" plugin.[/quote]

Thanks.  Apparently the metadata searcher plugin pings the 'net quite often to look for metadata.

Disabling the plugin gets rid of the skipping for me.  Also, having the system monitor on shows that I no longer ping the network at all due to banshee. (Before it was about once per second!

Banshee still has a high CPU utilization.  Just playing a song uses about 5-12% CPU utilization on my Athlon XP 3200+ system.  Changing from a playlist to my Music Library will take it up to 100% for a few seconds!

---

