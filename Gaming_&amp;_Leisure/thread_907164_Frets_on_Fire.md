---
title: "Frets on Fire"
date: 2008-09-01
forum: Gaming &amp; Leisure
---

### Post by forcerecon808 on 2008-09-01
I downloaded frets on fire from the unbuntu repositories, but when I click the icon, nothing happens, no error pop up, nothing. I have uninstalled and reinstalled but it's the same thing every time. What do I do?

---

### Post by forcerecon808 on 2008-09-01
Anyone?

---

### Post by ronnielsen1 on 2008-09-01
Just tried it and it worked fine. I'm suspecting a video problem with you. 


Type /usr/games/fretsonfire in a terminal. This will give you an error code which you need to copy and paste in this forum

---

### Post by forcerecon808 on 2008-09-01
> **ronnielsen1 said:**
> Just tried it and it worked fine. I'm suspecting a video problem with you. 


Type /usr/games/fretsonfire in a terminal. This will give you an error code which you need to copy and paste in this forum

This is what it said:
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Traceback (most recent call last):
  File "./FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 149, in __init__
    self.audio.open(frequency = frequency, bits = bits, stereo = stereo, bufferSize = bufferSize)
  File "/usr/share/games/fretsonfire/game/Audio.py", line 49, in open
    pygame.mixer.init()
pygame.error: No available audio device

---

### Post by ronnielsen1 on 2008-09-01
Type pasuspender fretsonfire in a terminal and see if it runs.

[http://ubuntuforums.org/showthread.php?t=779216](http://ubuntuforums.org/showthread.php?t=779216)

If it works it's easy to edit the menu to reflect it

---

### Post by ronnielsen1 on 2008-09-01
> I'm suspecting a video problem with you. 
It appears audio

---

### Post by forcerecon808 on 2008-09-01
> **ronnielsen1 said:**
> Type pasuspender fretsonfire in a terminal and see if it runs.

[http://ubuntuforums.org/showthread.php?t=779216](http://ubuntuforums.org/showthread.php?t=779216)

If it works it's easy to edit the menu to reflect it

Yeah, it worked, but thats seems to be the only way I can open it. How do I "edit the menu to reflect it"?

---

### Post by ronnielsen1 on 2008-09-01
Right click on the Ubuntu icon and left click edit menus. Scroll to Games > Frets On Fire and right click and then left click on properties. This will open a new window where you can change the command from /usr/games/fretsonfire to pasuspender fretsonfire

---

### Post by forcerecon808 on 2008-09-01
> **ronnielsen1 said:**
> Right click on the Ubuntu icon and left click edit menus. Scroll to Games > Frets On Fire and right click and then left click on properties. This will open a new window where you can change the command from /usr/games/fretsonfire to pasuspender fretsonfire

Now it opens, but when I press 'play' it says "list index out of range". Any idea what to do?

---

### Post by ronnielsen1 on 2008-09-01
Did you download frets-on-fire-songs-sectoid?
I'm sorry you're having trouble. It just downloaded for me but I have had trouble in the past. Are you using Ubuntu 8.04 or an older version?

[http://fretsonfire.wikidot.com/list-index-out-of-range](http://fretsonfire.wikidot.com/list-index-out-of-range)

> This error is mostly created by empty folders in /data/songs/ folder in your FoF directory or corrupted song.ini files.
 If you don't know which song is causing the problem and want a quick fix to make FoF work again, have the game select a different song on startup. To do this, follow these steps:
 1. Open fretsonfire.ini
2. Under [Game] find selected_song =
3. Clear the contents of it so that it displays "selected_song = "
 Doing the above will temporarily fix your error, but to actually resolve the problem, you're going to have to figure out which song is broken. The following will save you from having to go through every song folder indivdually checking it. Even so, this process might take a while if you have a lot of songs, so be patient.
 1. Try moving all songs out of the /data/songs/ folder to another place. Then move first ten folders back into /data/songs and try running FoF.
2. If it runs properly, close it and repeat step 1.

---

### Post by ronnielsen1 on 2008-09-02
Any luck?

---

