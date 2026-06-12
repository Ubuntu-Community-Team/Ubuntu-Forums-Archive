---
title: "MP3 music, rythmbox error"
date: 2006-01-24
forum: Desktop Environments
---

### Post by Garyu on 2006-01-24
Most of my MP3's work great. The sound in Ubuntu is better than in windows, and I really enjoy Rythmbox. However, some of my MP3's will play the entire song, and then freeze at the end so I have to manually press/click next song to make Rythmbox continue playing. And what is worse, some MP3's will actually hang Rythmbox so I have to keep shutting it down (forced) and then start it back up again. Very annoying. And even the music that hangs Rhythmbox will play all of the song, and then everything shuts down when Rhythmbox is about to change song. Something I noticed is that the sound is somewhat...eh...twitchy... it breaks up, like there wasn't enough computer power to process it, but I promise that there is nothing wrong with the computer power!

I tried to run 
```
checkmp3 Village\ People\ -\ YMCA\ \(Millenium\ Mix\ Almighty\).mp3
Possible ID3v2 frame found, skipping

FILE_NAME           Village People - YMCA (Millenium Mix Almighty).mp3
GOOD_FRAMES         21174
BAD_FRAMES          0
LAST_BYTE_CHECKED   8853964
SONG_LENGTH         18:26.23

```
But it looks normal to me. This is one of the songs that will hang Rhythmbox. Oh, hey, I just realized, the song_length from checkmp3 shows 18 minutes, but the song is only 9 minutes long... I realize that there might be something wrong with the files, but all of them have worked flawlessly in windows media player (some for years on end). And there are quite a lot of files showing this behaviour, so it would be a lot of work to identify them all and then rip them all over again...

Any ideas as to what I could try to solve this? All of my codecs and stuff were downloaded with Automatix (or whatever it's called, the script-thing).

---

### Post by endersshadow on 2006-01-24
Try editting the metadata of the mp3 with easytag:

```
sudo apt-get install easytag
```

Make sure you correct the length of the songs.  You don't need it down to the hundredth of the second, but to the second is more than sufficient (just truncate).  Otherwise, Rhythmbox is looking to play a song that's 18 minutes long and can't find the last 9 minutes of it and gives up...

---

### Post by Garyu on 2006-01-24
[QUOTE=endersshadow]Try editting the metadata of the mp3 with easytag:

Make sure you correct the length of the songs.  You don't need it down to the hundredth of the second, but to the second is more than sufficient (just truncate).  Otherwise, Rhythmbox is looking to play a song that's 18 minutes long and can't find the last 9 minutes of it and gives up...[/QUOTE]

Wow, easytag is a really  nice piece of software that I hadn't discovered. Thank you for the tip, it was already installed so I just explored it now. However, it does not fix my problem. Easytag and Rhythmbox both report the above song to be 9 minutes, which Windows Media Player also does, but which checkmp3 does not (18 minutes instead). Also, even though easytag seems to report the correct time from the file, I still couldn't find a way to edit this.

I have tried to understand more about this, and I think I have found a common pattern. Many of the songs that will cause Rhythmbox to stop playing at the end of the song (so I have to press next song to continue listening) will hang Rhythmbox completely if I do not press the "next" button. The time it takes for Rhythmbox to hang is different between different songs. In my Village People example, Rhythmbox hangs almost immediately, while other songs may be just standing still for about 10 minutes or so (all the while reading from the hard disk) and then completely hanging Rhythmbox.

---

### Post by Garyu on 2006-01-26
I still have this problem. If I press "next song" when Rhythmbox stops at the end of the song it won't freeze, but sometimes I have to press up to 3-4 times before Rhythmbox decides to move on to the next song. This is very annoying since I can't leave my computer on with continous music playing as I normally do... :(

---

### Post by Garyu on 2006-01-27
haha, finally, problem solved... as it seems at least. :)

what I did was, since the Preferences section in Rhythmbox is somewhat limited, I decided to try a different player where I could play around with some different settings. So I opened up Beep Media Player, which seems to be a great player btw if you like the WinAmp interface, and there I changed the sound from OSS to ALSA... After that it worked like a breeze in Beep and when I started Rhythmbox afterwards it works great there too! =)

I've got to tell you though, people are talking about Linux as "more control" and "I want to know exactly what is happening" but to me it just seems like there are random events that make things work. :P

---

